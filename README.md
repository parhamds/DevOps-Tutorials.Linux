# Useful Bash Commands and Tips

Here's a collection of useful Bash commands and tips for various tasks:

## Creating a File

To create a new file, you can use the `touch` command:

```bash
touch file_name
```

## Bash If Statement Example

Here's an example of using an if statement in a Bash script:

```bash
#!/bin/bash

Name=$1
Visibility=$2

if [ "$Visibility" = "true" ]; then
    echo "My name is $Name"
else
    echo "Make visibility true"
fi
```

Make sure to make the script executable:

```bash
chmod +x sc.sh
```

And execute it:

```bash
./sc.sh parham true
```

## Downloading Files

You can use `wget` to download files:

```bash
wget <link>
```

## Adding User to sudoers

To add a user to sudoers, edit the sudoers file:

```bash
vim /etc/sudoers
```

And add the following line:

```
jenkins ALL=(ALL) NOPASSWD: ALL
```

## Installing Packages on Linux

To install a package from a tar.gz file, follow these steps:

```bash
wget <bin.tar.gz_link>
tar -xvzf <file_name>
mv <extracted_folder_name> /opt/
vim ~/.profile
```

Add the following lines at the beginning of the file:

```bash
M2_HOME='/opt/<extracted_folder_name>'
PATH="$M2_HOME/bin:$PATH"
export PATH
```

Then, source the profile:

```bash
source ~/.profile
```

## Viewing Folder Structure as a Tree

You can use the `tree` command to see the content of a folder as a tree:

```bash
apt install tree
tree <folder_name>
```

## Changing User

To change the user, use `sudo -iu`:

```bash
sudo -iu jenkins
```

## Generating SSH Keys

Use `ssh-keygen` to generate SSH keys:

```bash
ssh-keygen -t rsa
```

## Installing a Specific Version of a Package

You can install a specific version of a package using `apt-get`:

```bash
sudo apt-get install kubeadm=1.21.1-00
```

## Converting Text to Base64

To convert text to Base64, you can use the `base64` command:

```bash
echo -n '<text>' | base64
```

## Viewing Service Logs

To view logs of services, you can use `journalctl`:

```bash
sudo journalctl -u kubelet -f
```

## Writing to a File

To append to a file, you can use `echo` with `>>`:

```bash
echo ${aws_instance.MyFirstInstnace.private_ip} >> my_private_ips.txt
```

## Adding Volume and Auto-Mounting

To add a volume and auto-mount it, follow these steps:

```bash
mkfs.ext4 <disk_name>
mkdir -p /data
mount <disk_name> /data
```

Check the disk usage:

```bash
df -h
```

Edit `/etc/fstab` to auto-mount:

```
<disk_name> /data ext4 defaults 0 0
```

## Running a Program and Logging Output

To run a program and log the output to both stdout and a file, use `tee`:

```bash
./program | tee <logfile>
```

## Stress Testing

You can stress test using the `stress` command:

```bash
apt install stress
stress --cpu 2 --timeout 300
```

## Setting and Unsetting Environment Variables

To set an environment variable:

```bash
export <env_var>=<value>
```

To unset an environment variable:

```bash
unset <env_var>
```

## Sleeping Until Instance is Ready

Use a loop to sleep until the instance is ready:

```bash
until [[ -f /var/lib/cloud/instance/boot-finished ]]; do
    sleep 1
done
```

## Generating SSH Keys with Specific Names

To generate SSH keys with specific names:

```bash
ssh-keygen -f levelup_key
```

## Viewing Existing Groups and Users

To see existing groups:

```bash
cat /etc/group
```

To see existing users:

```bash
cat /etc/passwd
```

## Creating a File with Arbitrary Size

You can create a file with an arbitrary size using `fallocate`:

```bash
fallocate -l 15G temp_file
```

## Stress Testing in Linux

To stress test in Linux, you can use `stress-ng`:

```bash
sudo apt install stress-ng
stress-ng -c 2 -v --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.85;}' < /proc/meminfo)k --vm-keep -m 1 --timeout 300s
```

Feel free to copy and paste these commands into your terminal for easy reference!