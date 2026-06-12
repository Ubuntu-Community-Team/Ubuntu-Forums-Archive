---
title: "upgrade backup assistance needed"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by dBuster on 2010-06-03
Okay, after playing with 10.04 LTS on the wife's netbook, I am wanting to upgrade my 9.04 laptop.  One thing, I can not go directly to 10.04 without a clean install and doing the step to step upgrade is not recommended from my reading.  There are just some quirks about 9.04 on my laptop that I would like to get away from, such as any kernel updates I have to re-install my nVidia drivers and then re-build my madwifi setup in order to be back up and running.  I guess I could build a script to run and have it do all that instead of my going line by line, but if I didn't have to worry about it even better yet.

With that in mind, I am wanting to back up my settings and files.  If I back up my "/home" folder, ie burn it backed up to a dvd, will that work?  

Or would it cause me to re-install everything back with the new 10.04 install? 

If I did re-install everything and then restored the data back to the hard drive would the re-installed programs utilize the customized settings from the restored backup?

Would it be more beneficial if I gparted the drive and created a separate volume for my data to reside in and moved the /home folder there?

Sorry for all these noob questions but I do not want to hose everything up and then be in a bind.  Took me long enough to find a release that would work on this laptop to begin with.  I got it back when 8.04 was the latest release and suffered through Vista until 9.04 alpha 2 came out and that worked so I kept with 9.04 through the final.  I just like using a LTS as my last laptop before the video died on it was a LTS release as well.  Something about long term support...

Thanks in advance to anyone who answers.  Hopefully I will get some guidance from the Ubuntu masters!

Also one more - what is the best way to adjust partitions in your opinion?  To use windows to resize or gparted?  I want to reduce the windows partition and give more to Ubuntu!

---

### Post by dBuster on 2010-06-03
How sad it is to read some of the posts here where others are not doing upgrades properly and trying to skip a release.  

So many floods of postings as well causing some who do not get a reply to bump their posts...  Only 11 hours old and already back on page 7 of the thread...

---

### Post by georgemc on 2010-06-04
dBuster,

this is what I did, and at the end are my notes on various items.  I hope it helps.

george

P.S. I used this from 9.04>10.04 and 9.10>10.04

<<<>>>>
                                 Upgrading to new version of Ubuntu.
 Should apply to *NIX in general.
 

 This is a guide, that works for me, and not a copy/paste Howto.
 

 Instead of just hitting the &#8220;upgrade now&#8221; button in the &#8220;Update manager&#8221;, I will clean install the new OS on the current OS's partition.  This will reformat the current OS partition and therefore all data WILL be lost on that partition.  At the same time I do want to keep all my customization and all those extra home brew programs and packages I installed.
 

 There are implications with encrypted Home directories, encrypted HD's, Raid Arrays, Wubi, Dual Booting, and what have you, that I will not address here.  I think there are more knowledgeable people on these forums for those aspects.
 

 **Pre-upgrade preparation:**
 

 In preparation of a clean install I have setup my systems with a separate Home partition and backed up various configuration and data files.
 

 _Making a new Home partition:_  
 Load the &#8220;live&#8221; CD and simply make a new partition and I use rsync -rlpAXogt &#8220;SRC&#8221; &#8220;DEST&#8221; to copy my home directories to the new partition.  Add the partition in the /etc/fstab file and make sure you boot up and correct any errors that may occur before proceeding.
 

 Copy any of your configuration files and directories to your home directory for save keeping. For example see my configuration file list below.  Your list will vary depending on your own unique setup.  Worse case you might have to configure an application or package from scratch or retrieve them from a backup.
 

 The final preparation step is to start Synaptic and save your packages in your home directory.  Launch Synaptic and goto File > Save markings as &#8230; , make sure you checked the &#8220;Save full state, not only changes&#8221; check box, and save the list.
 

 **Backup &#8211; Backup &#8211;  and Backup:**
 Now would be a good time to backup your home directories and other data to an off-line or separate media.
 

 **Upgrade:**
 If you feel you have saved all your custom configurations and data, never hurts to double check, have at it and clean install the new OS.
 

 Follow the install script and specify the partitions manually.  If you are unsure which partition is what then nows the time to quit and verify.
 

 Identify your old OS partition, I mark it for format, and the mount point is &#8220;/&#8221;.  Identify your Home partition and make sure you DO NOT mark it for formating, and the mount point is &#8220;/home&#8221;.  Double check your settings and hit that &#8220;forward&#8221; button.
 

 It is easier for me to just recreate the users in the order I initially created them, so the first user gets UID 1000 and lines up with the file permissions in my home directory.
 

 You are given one last chance to cancel or quit the upgrade.  Once you mash the &#8220;install&#8221; button there is no turning back.
 

 **Post-upgrade:**
 

 Let the system boot and when you are logged in and on-line check for updates.  When all the OS updates are completed import the Synaptic file you saved earlier and let Synaptic re-install all your packages.  Check the differences of the new configuration files with your save ones, don't just blindly copy them over.
 

 Reinstall your home brew and check its functionality.  There can be differences between the releases when it comes to the various programs and their behavior.  Some adjustments may be necessary.
 

 I choose to reboot after every major section, i.e. between the install and the updates, just to ensure that I only have to trouble shoot one section at a time.
 

 The first hurdles to overcome are X11 and screen resolution, and network connectivity.  On my desktops I need to identify my monitor to get the resolution I desire, and on my laptop I nailed up my WiFi to connect only to my WiFi node automatically.  Once you get past this you should be able to update and reload your packages and enjoy the new OS.
 

 Keep in mind that there will always be that one package/program suit that requires re-installation no matter what you saved.  However, since you saved the configuration files it should be easy to re-install and configure.
 

 _My &#8220;to be saved&#8221; configuration file list_:
 

 /etc/passwd
 /etc/group
 /etc/samba/smb.conf
 /opt/nessus  
 /etc/X11/xorg.conf
 /etc/fancontrol
 /etc/sensors.conf
 /etc/network/interfaces
 /etc/smartd.conf
 /etc/exports
 /etc/fstab
 /etc/nsswitch.conf
 /etc/apt/sources.list
 /usr/local/bin
 /etc/udev/rules.d/91-local.rules
 /var/log/bootchart
 

 

_Notes to myself on the various backed up and configuration items_:


 Home directory.
 Make sure and move the home directories to their own partition.
 Backup the home directories.
 

 Music, Still PIX, Movies.
 Make sure that this data is either in home directories or their own partition.
 Backup the data directories.
 

 Users configuration.
 Either remake all the users on the new system in the same order as before or manually change the UIDs in /etc/passwd .  Probably only the ID's 1000 and greater are the ones we want to save.  Save and backup the /etc/passwd file.
 

 Groups configuration.
 Save and backup the /etc/group file.  Probably easier to just edit the newly created file and match the UIDs in the file.
 

 Wifi configuration.
 Save and backup the /etc/network/interfaces file.  Only necessary with static IP's  and nailed up WiFi's.
 

 Samba configuration.
 Backup and save the /etc/samba/smb.conf file with all its configurations.
 

 Nessus configuration.
 Backup and save the /opt/nessus directory with all its configurations.
 

 VMWare
 Check Vmplayer and the &#8220;Virtual Machine Settings&#8221; and make sure the images are on a safe partition i.e. in the home directory or on their own partition.  Backup and save them.
 By default they are in &#8220;/var/lib/vmware/Virtual Machines&#8221;
 Note: moved to DataDisk
 

 VBOX
 Check the &#8220;Virtual Media Manager&#8221; and make sure the images are on a safe partition i.e. in the home directory or on their own partition.  Backup and save them.
 By default they are in &#8220;~/.VirtualBox/HardDisks&#8221;.  Should be taken care of with the &#8220;home&#8221; directories.
 

 Xorg  
 Backup and save the &#8220;/etc/X11/xorg.conf&#8221; file.  If X starts with the proper resolutions then we can disregard this.
 

 Email (Evolution)
 Data should all be in your home directory.
 

 Sensors & Fancontrol
 Backup and save &#8220;/etc/fancontrol&#8221; and &#8220;/etc/sensors.conf.
 

 Packages
 In &#8220;Synaptic&#8221; run &#8220;Save Markings&#8221; and check &#8220;Save full state, not only changes&#8221; and save it to your home directory.

---

