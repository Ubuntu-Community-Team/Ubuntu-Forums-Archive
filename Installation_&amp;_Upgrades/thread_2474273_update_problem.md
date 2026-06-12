---
title: "update problem"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2022-04-25
I run my updates and upgrades manually, every day, and have seen an issue for the last few days. I run apt list --upgradeable after my update and see the same to packages to be upgraded;
```
Listing...mkusb-plug/focal,focal 12.7.3-1ubuntu3 all [upgradable from: 12.7.2-1ubuntu1]
mkusb/focal,focal 12.7.3-1ubuntu3 all [upgradable from: 12.7.2-1ubuntu1]



```

I use a script to do my upgrades, so I ran a second time this morning, after upgrading, and the same 2 packages are listed. I ran everything separately and got the following output;
```
charles:$  sudo apt update[sudo] password for charles: 
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease      
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:4 http://ppa.launchpad.net/dupeguru/ppa/ubuntu focal InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:6 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:7 https://esm.ubuntu.com/infra/ubuntu focal-infra-security InRelease
Hit:8 https://esm.ubuntu.com/infra/ubuntu focal-infra-updates InRelease
Hit:9 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
Hit:10 http://archive.canonical.com/ubuntu focal InRelease     
Reading package lists... Done                                  
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
charles:$ apt list --upgradeable
Listing... Done
mkusb-plug/focal,focal 12.7.3-1ubuntu3 all [upgradable from: 12.7.2-1ubuntu1]
mkusb/focal,focal 12.7.3-1ubuntu3 all [upgradable from: 12.7.2-1ubuntu1]                                                        
charles:$ sudo apt upgrade                                      
Reading package lists... Done                                   
Building dependency tree                                        
Reading state information... Done                               
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms efibootmgr libfwupdplugin1 libgsoap-2.8.91
  liblua5.3-0 liblzf1 libsdl-ttf2.0-0 libvncserver1
  pushover-data virtualbox-dkms
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  mkusb mkusb-plug
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Is there a reason I continue to be shown these can be upgraded, but my system not upgrading them? I'm a little confused. Everythng returns exit code 0,so why is it not upgrading mkusb?
Any insight and/or advise greatly appreciated. Thanks

---

### Post by deadflowr on 2022-04-25
Have you tried running it with apt full-upgrade instead of apt upgrade?

apt upgrade can install new packages, but will not remove old packages if that is required to install the new packages.
apt full-upgrade will install new packages, and will remove old packages if that is required.

---

### Post by scubascooby on 2022-04-25
Sorry replied to wrong thread.

---

### Post by rbmorse on 2022-04-25
*** withdrawn ***

---

### Post by #&amp;thj^% on 2022-04-25
```
sudo apt remove mkusb 'mkusb-*' usb-pack-efi
```
followed by:
```
sudo apt autoremove
```
providing it was installed through the PPA "ppa:mkusb/ppa"
if not sudodus has a script to un-install as well:
```
sudo ./dus-installer r  # remove
```
that is run from the same install directory/folder.
Then if necessary reinstall the package/s

---

### Post by coley9225 on 2022-04-25
Thank you for the help. I didn't think to try full-upgrade. That fixed the problem, and I'll mark this one as solved.

---

### Post by GhX6GZMB on 2022-04-25
I've created a little script in /usr/sbin called upgrade
It contains this:

```
#! /bin/bash
sudo apt update && sudo apt upgrade && sudo apt autoremove
```

This works perfectly for my bi-weekly upgrades.
Permissions: rw------- root:root

Command line:

```
sudo upgrade
```

---

### Post by deadflowr on 2022-04-25
> **ml9104 said:**
> I've created a little script in /usr/sbin called upgrade
It contains this:

```
#! /bin/bash
sudo apt update && sudo apt upgrade && sudo apt autoremove
```

This works perfectly for my bi-weekly upgrades.
Permissions: rw------- root:root

Command line:

```
sudo upgrade
```

The OP is using a script much the same (as explained in post #1), but the issue here was the upgrade needed to do more than what plain apt upgrade can do.
Also why doesn't your script just stop at the sudo apt upgrade command?
Which it should since you are required to answer yes (Y) or no (n) to proceed with that command.

---

### Post by GhX6GZMB on 2022-04-25
> **deadflowr said:**
> 
Also why doesn't your script just stop at the sudo apt upgrade command?
Which it should since you are required to answer yes (Y) or no (n) to proceed with that command.
Because I run it manually. And the Y/N is not an issue. I like to see what's being changed before proceeding.
It's no more than a shortcut sparing me entering three different commands.

---

### Post by deadflowr on 2022-04-25
> **ml9104 said:**
> Because I run it manually. And the Y/N is not an issue. I like to see what's being changed before proceeding.
It's no more than a shortcut sparing me entering three different commands.

Okay, so basically no different than setting an alias.

---

### Post by coley9225 on 2022-04-26
ml9104, I have a script that does all of that. Updates, list upgradeable, upgrades and checks if reboot is needed.

```
#! /bin/bash

shopt -s nocasematch  # make responses case insensitve


FILE1=/var/run/reboot-required
# A short script to simplify my updates.
# Must be run as root with sudo.


function_restart () {
    echo "You will need to reboot your computer to complete the upgrade. The following packages require a reboot to fully install your upgrades."
    cat /var/run/reboot-required.pkgs
    echo "Do you want to reboot now?: [y/n]:"
    read yn
        case $yn in
            
            y | "")
                echo "Your computer will reboot now."
                sleep 5
                reboot
                ;;
            n)
                echo "Your system reboot will be postponed for now."
                ;;
                
            *)
                echo "Invalid option. Your computer will NOT reboot at this time." ;;
            
        esac
}
    
/usr/bin/apt update &&
echo "exit status $?" &&


/usr/bin/apt list --upgradable | tee ./upgradable_list.txt
echo "exit status $?"


echo -n "Do you want to upgrade now? [y or n]: "
    read yno


    case $yno in
        
        y | "")
            /usr/bin/apt upgrade -y
            echo "Exit status $?"
            ;;
        n)
            echo "We will postpone upgrades for now."
            ;;
        *)
            echo "Improper response. Please run upgrade manually.
            Exiting script now. Exit 1."
            ;;
    esac


if test -f "$FILE1" ; then
function_restart
fi
echo "Your all done for today"
sleep 5
exit



```

The entire process is interactive, so you decide whether to do each step or not. Your OS may use a different file for reboot-required, maybe reboot-needed, or similar. Please feel free to use this script if you would like. I created a shortcut, '<super>+<U> to run command 'qterminal -e sudo path/to/script'. If use use a different terminal emulator you will need to change that. It has been suggested that I modify the script and run as a cron job, but I, like you, like to see what is being upgraded and decide whether to do it now or wait. Good luck.
p.s. I may change the apt upgrade -y to apt full-upgrade -y, haven't decided yet.

---

