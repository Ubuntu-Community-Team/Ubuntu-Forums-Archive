---
title: "Update Fails"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by markdayton on 2008-06-16
Update Fails.  When run from terminal I get the following:

root@ubuntu:/home/ubuntu# apt-get update
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Tran
slation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing dpkg-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5                                      f%20-%20Release%20i386%20(20080423)_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

System: Dell Inspiron E1503, Kubuntu 8.04 installed on USB drive.

Any suggestions?  This broke a couple weeks ago, before that the updater seemed to work properly.  Being new to Linux I'm in that stage where every time I touch it it gets worse.  I appreciate any help you can give.

---

### Post by iaculallad on 2008-06-16
On your terminal, try copying the old dpkg status file:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.original.renamed
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by markdayton on 2008-06-16
Thank you so much for your quick reply. Here are my results:

root@ubuntu:/home/ubuntu# sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.original.renamed
root@ubuntu:/home/ubuntu# sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
root@ubuntu:/home/ubuntu# sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing dpkg-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080423)_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by iaculallad on 2008-06-16
Try to delete the old list files and redo update:

```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update && sudo apt-get upgrade

```


Or if that would fail, try the other option below:

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by markdayton on 2008-06-16
Thank you for your continued assistance. Neither option worked.

Here are my results:

root@ubuntu:/home/ubuntu# sudo rm -vf /var/lib/apt/lists/*
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080423)_dists_hardy_main_binary-i386_Packages'
removed `/var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080423)_dists_hardy_Release'
removed `/var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080423)_dists_hardy_Release.gpg'
removed `/var/lib/apt/lists/Kubuntu%208.04%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080423)_dists_hardy_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages'
root@ubuntu:/home/ubuntu# sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages [1178kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [25.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6156B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [12.7kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [6918B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [906B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages [6986B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages [4297kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources [338kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources [1488B]
Fetched 5998kB in 37s (160kB/s)
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/home/ubuntu# sudo apt-get update -o APT::Cache-Limit=25165824
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Syntax error /var/lib/apt/cdroms.list:7: Extra junk at end of file

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-06-16
Ok, we try this:

Navigate to K menu->System->Adept Manager, Under "View"->"Manage Repositories". Locate something w/c says or equivalent to "Installable from CD-ROM/DVD" and uncheck it. Close the window and redo your update. 

Then:

```
sudo apt-get update && sudo apt-get upgrade
```


(Im using Ubuntu so I can't actually picture Adept)

better yet, try to post your sources.list file if that does not work.

```
kate /etc/apt/sources.list
```

---

### Post by markdayton on 2008-06-16
After getting a bunch of files, unpacking, and setting up I get the following:

Preparing to replace sudo 1.6.9p10-1ubuntu3 (using .../sudo_1.6.9p10-1ubuntu3.2_i386.deb) ...
Unpacking replacement sudo ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.


Thank you again for your support.  I'm going to have to call it a night and pick this up in the morning.

---

### Post by markdayton on 2008-06-17
Good morning.  After rebooting I tried running Adept Manager to Fetch Updates and it wouldn't start saying that another process is using the packaging system.  I pressed Yes "to attempt to resolve this problem" and got a message saying that Adept Manager (adept_manager) crashed and caused the signal 6 (SIGABRT).  I then tried running it from the terminal with sudo apt-get update && sudo apt-get upgrade and got the following error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. So I ran the suggested command which seemed to run without any errors (that's progress!). So I re-ran sudo apt-get update && sudo apt-get upgrade and got the following: 

110 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 739kB/95.3MB of archives.
After this operation, 672kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libedataserver1.2-9 2.22.2-0ubuntu2 [113kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libcamel1.2-11 2.22.2-0ubuntu2 [304kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libebook1.2-9 2.22.2-0ubuntu2 [79.6kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libecal1.2-7 2.22.2-0ubuntu2 [242kB]
Fetched 739kB in 3s (191kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 122326 files and directories currently installed.)
Preparing to replace sudo 1.6.9p10-1ubuntu3 (using .../sudo_1.6.9p10-1ubuntu3.2_i386.deb) ...
Unpacking replacement sudo ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.

So that's where I'm at this morning - still broken and heading back to Windows for the day.  I'll be back to bang my head on this again this evening Roanoke, Virginia, USA time.

---

### Post by markdayton on 2008-06-17
Any suggestions on how to terminate the incomplete installation, and deal with the segmentation fault caused by the replacement sudo?

---

### Post by iaculallad on 2008-06-17
Try to download [sudo_1.6.9p10-1ubuntu3.2_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.2_i386.deb") file and do a single file installation file if it could resolve the sudo error thing.

After your successful file download, try to get in your terminal and change directory to your Desktop:

```
cd ~/Desktop
sudo dpkg -i sudo_1.6.9p10-1ubuntu3.2_i386.deb
```

Im not quite sure if this will your case.

---

### Post by markdayton on 2008-06-18
Thank you for all your help.  After I booted up Kubuntu last night (this was the second boot since my last post of the sudo error), Adept ran without complaining about another instance and it fetched and installed updates without any errors. However, when I tried to run Full Upgrade it failed.  After a couple more reboots I tried just upgrading a handful of files and it also failed. After a dozen or so reboots, system crashes, failed reboots, and more errors, I'm left with a blue screen, a mouse pointer, and nothing else.  At this point I have given up.  Again, thank you for taking the time to help me.

---

