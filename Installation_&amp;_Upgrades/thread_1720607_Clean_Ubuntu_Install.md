---
title: "Clean Ubuntu Install"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Shadow Warrior on 2011-04-03
I'm having ongoing problems with my Ubuntu installation(s) almost to the point that each addition causes new problems. The latest, continual problem is periodically the computer is being used and abruptly hangs with a blank screen. Though I believe the error is associated with my having an undefined ServerName for LAMP development server. I've decided to do a fresh install with all the options included and see what happens. I need some assistance in developing an install CD/DVD which has all the packages (and configurations) that I need. A volunteer would greatly be appreciated. Instead of detailing my full configuration here, would someone who is up to the task contact me to assist.

I want to be able to use a serial mouse (the computer is an older one and I only have a serial mouse to use).

---

### Post by oldfred on 2011-04-03
I prefer to do clean installs and have found a few things that help. I just use the standard Ubuntu Cd but have backed up certain data to copy into the new install. I do install to a new / (root) so I can reboot my old install in case I have forgotten something.

My backups include these files:
echo "starting..."
# So I know additional sources
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
# List of all installed applications
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files
# System Boot Configuration
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh

Some suggested this:
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

I do not copy back files from /etc and usually only copy into my /home files I have manually edited so they get backed up. My new installs may not use all the same config files so I do not just copy back, unless I know I need the setting. 

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I back up a list of all installed packaged. List is just names not versions, so new Ubuntu version will install the new version of the app. May need editing as Natty for example now uses Libreoffice and list still has Openoffice & I know I do not want both.
List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

---

