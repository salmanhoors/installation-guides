# Jenkins Installation on Amazon Linux 2023 6.1 AMI
-----------------------------------------------------------
sudo dnf update -y
sudo dnf install java-17-amazon-corretto-devel -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf install jenkins -y
sudo systemctl daemon-reload
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

Setup Jenkins
Access Jenkins on 8080 Port

If you find the node offline; follow the below
This error occurs because Jenkins monitors disk space by default, and your /tmp partition is running low. On Amazon Linux 2023, the /tmp directory is mounted in memory (tmpfs) by default, which is limited even though you have a 30GB EBS volume.
Method 1 (Recommended)
# Create a new /tmp directory on your EBS volume
sudo mkdir /mnt/tmp
sudo chmod 1777 /mnt/tmp

# Move the existing tmp contents
sudo rsync -av /tmp/ /mnt/tmp/

# Update fstab to use the new location
echo "none /tmp tmpfs defaults,size=2G 0 0" | sudo tee -a /etc/fstab

# Reboot to apply changes
sudo reboot


# Jenkins Installation on Ubuntu 24.04 AMI
-----------------------------------------------------------
sudo apt update -y
sudo apt install fontconfig openjdk-17-jre -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update -y
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
