---
title: "autoinstall not running late_command curl on /target"
date: 2021-02-20
forum: Installation &amp; Upgrades
---

### Post by johnbradford on 2021-02-20
We're a small charity, repurposing laptops to support kids' education over the COVID pandemic. We've been using Ubuntu for our coding club laptops since we started 5yrs ago.

We've repurposed nearly 700 laptops but it's a bit of a faff. First we use DBAN, then install Ubuntu, then run a configuration digi_auto.sh script. I'd like to get to a single usb install for a desktop image.

I've got a (nearly) working cloud-init but while it runs the digi_auto.sh file (I know this because part of the script registers on rudder.io for update management), when I log in after the install, it's like the config script never happened. I'm assuming it's running on the usb image in memory which is obviously lost when the usb comes out and I boot from hdd.

The .sh file is basically a cut'n'paste from the one we use at the moment from terminal.

The reason I'm doing it this way, is that I have a working .sh install script that I'd like to keep and I don't really want to spend the time trying to get everything into a cloud-init user-data file.

I'm building the iso from the builder script on github: [https://github.com/covertsh/ubuntu-autoinstall-generator](https://github.com/covertsh/ubuntu-autoinstall-generator)

What I'd like is a simple usb that I can hand out to volunteers to do everything in one hit. I've taken out the early_command for shred to speed up testing. It 'runs' without errors, but doesn't do what I think it should do. I've tried putting the curl part in ' ' but then it throws a non-zero 127 error.

Are there any 'obvious' gotcha's in my files, and how do I get the install to run on the laptop image?

This is my user-data file
```
#cloud-config
autoinstall:
  version: 1
  geoip: true
  identity:
    hostname: digiadmin
    password: $6$ocHMJ9ir83epkz44$u1xqzpImhEC6aGAZb5dUDjgXOr/iYipwvMSqMQPTxFAMvmqZsiDmVT3DRDLdqb/U2tBXJN80Kjd5JwqhrdAg6.
    username: DigiAdmin
  timezone: Europe/London
  keyboard:
    layout: en
    variant: uk
  locale: en_GB.UTF-8
  apt:
    preserve_sources_list: false
    primary:
      - arches: [amd64]
        uri: "http://archive.ubuntu.com/ubuntu/"
  packages:
    - build-essential
    - ubuntu-desktop
    - curl
  late-commands:
    - curtin in-target --target=/target -- usermod -p [...] root
    - curtin in-target --target=/target -- curl https://raw.githubusercontent.com/jwgbradford/rudder-techniques/master/digi_auto.sh | /bin/bash -s
    - poweroff

```

and this is the digi_auto.sh file that it should run on /target
```
#!/bin/bash
add-apt-repository multiverse
apt update

##install extra apt packages
apt install wget python3-pip apt-transport-https gdebi openjdk-11-jdk

##install .deb packages
wget -P /home/digiadmin https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
gdebi /home/digiadmin/google-chrome-stable_current_amd64.deb --non-interactive
rm -f /home/digiadmin/google-chrome-stable_current_amd64.deb

wget -P /home/digiadmin https://zoom.us/client/latest/zoom_amd64.deb
gdebi /home/digiadmin/zoom_amd64.deb --non-interactive 
rm -f /home/digiadmin/zoom_amd64.deb

##set desktop favourites
wget -P etc/dconf/profile/ https://raw.githubusercontent.com/jwgbradford/rudder-techniques/master/user
wget -P /etc/dconf/db/local.d/ https://raw.githubusercontent.com/jwgbradford/rudder-techniques/master/00-favourite-apps

##set ufw to default
ufw enable

#SERIAL=$(sudo dmidecode -t system | grep Serial)
#set -- $SERIAL
#Get serial number of laptop
SERIAL=$(sudo dmidecode -s system-serial-number)
NEWHOSTNAME='digilocal-'$SERIAL
#Set hostname
hostnamectl set-hostname $NEWHOSTNAME

#install rudder.io agent
wget --quiet -O- "https://repository.rudder.io/apt/rudder_apt_key.pub" | apt-key add -
echo "deb http://repository.rudder.io/apt/6.2/ $(lsb_release -cs) main" > /etc/apt/sources.list.d/rudder.list

apt-get update
apt-get install rudder-agent -y
echo '104.248.170.79' > /var/rudder/cfengine-community/policy_server.dat
rudder agent inventory
rudder agent home

##final update and cleanup
apt update
apt full-upgrade -y

```

---

### Post by ActionParsnip on 2021-02-20
Could use a preseed file to configure systems or have the files accessible on a local file server or available via http on the Web. You can then wget from that when they are out and about.

---

### Post by ActionParsnip on 2021-02-20
Just reviewing your script. It looks fine. You missed a leading slash on the first wget command but it's all grabbing from the Web which is fine

---

### Post by johnbradford on 2021-02-21
Think the preseed method has been deprecated and cloud-init is the preferred option.

---

### Post by johnbradford on 2021-02-21
I did also try in user-data basically my terminal method:
wget - /target/run https://
chmod +x /target/run/digi_auto.sh
/target/run/digi_local.sh

but that didn't work either - couldn't find the file

---

