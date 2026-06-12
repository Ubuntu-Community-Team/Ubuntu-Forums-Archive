---
title: "Problem MBR and partition FAT 32 duo boot with windows 7"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by olivierhenry on 2014-03-07
Hello everyone ,

I now have 2 different problems for which I wish a reply.
I am looking to get a dual boot Windows 7 and xubuntu with a common partition for both OS.
Firstly I just installed xubuntu on a laptop Asus U31SG with a 1TB hard drive (no optical drive).
I proceeded in the following manner.
I installed a new hard drive, I installed Windows 7 from a USB key image.
I partitioned the hard drive to reduce the allocated space for windows.
Then I installed ubuntu from another image on a USB key .
During the installation, I allocated a portion of the disk for root / ( ext4 ),
a portion to the swap, a portion to /home ( ext4 ) and 500GB for both OS which I put in /windows (Fat 32).
I then completed the installation, removed my USB key while turning off the laptop.
Note, I did not have access to my 500GB partition but access to the NTFS partition (windows partition) while under ubuntu.
Another problem appeared. When I booted, I ended up directly to windows, with recognition of the partition of 500GB (Fat 32) under windows .
So I had no access to Ubuntu anymore. As a result, I decided to repair the MBR with Boot- Repair.
I used the default choice, sda.
The repair let me have access to Ubuntu but I lost access to windows .
In conclusion, I am looking to repair the MBR. I know it is possible to reinstall the MBR of windows but I will lose my access to ubuntu and I'm afraid to come back to square 1.
Beside, I would like to know how to format my 500GB partition in a way that it is recognized by both OS.
Thank you for any help.

Olivier

---

### Post by westie457 on 2014-03-07
The 'easy' bit is to reformat the 500GB partition as NTFS.

The 'hard' part is to now get you access to both systems. Can you post the link to your Boot info report. If you did not take note of the first one run Boot Repair again. Go to 'advanced' options, say no to all repairs and accept the option to create the report.

---

### Post by olivierhenry on 2014-03-07
Thank you so much for the quick reply.
Here is the report
[http://paste.ubuntu.com/7053196/](http://paste.ubuntu.com/7053196/)

---

### Post by oldfred on 2014-03-08
Other than missing Windows, install looks ok. 

I would also suggest not using FAT32 but change to NTFS. 
You can reformat and change fstab entry to mount NTFS instead of vfat. FAT does not have journal so chkdsk repairs may not work or be very slow. And you cannot save any file over 4GB.

Usually the install runs os-prober and adds the Windows entry. But you can just rerun it with an update to grub.

From terminal:
sudo update-grub

---

### Post by olivierhenry on 2014-03-08
Thank you for your answer.
I updated the grub and reformated the 500Go volume to NTFS.
So now I have access to windows OS and the 500Go volume appears in ubuntu.
But there is still a problem at the start up of ubuntu
"The disk drive for /windows is not ready yet or not present
Continue to wait, or Press S to skip mounting or M for manual recovery" 
I tried to fix the problem with ntfs-config on sda7 but I could not make a change with it, the program does not allow me.
Here is the message on the terminal
olivier@olivier-U31SG:~$ sudo ntfs-config
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/NtfsConfig/AddWizard.py", line 159, in on_auto_clicked
    self.auto_configure()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/AddWizard.py", line 168, in auto_configure
    self.disk.savelog()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/Fstab/FstabHandler.py", line 522, in savelog
    self._logconf.add_section(name)
  File "/usr/lib/python2.7/ConfigParser.py", line 260, in add_section
    if section.lower() == "default":
AttributeError: 'float' object has no attribute 'lower'

---

### Post by oldfred on 2014-03-08
The ntfs-config has not been maintained for ages, so you often do not get correct parameters. You really just need to make a minor change to your mount in fstab from vfat to ntfs, but I might also change a few parameters.

       [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

 For ntfs UUID shown is example only see below:
> UUID=XXXXXXXXXXX   /windows ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Your current entry in fstab. Your UUID also changed when you reformatted it:
> 
 /windows was on /dev/sda7 during installation
UUID=79F6-E69F  /windows        vfat    utf8,umask=007,gid=46 0       1

sudo cp /etc/fstab /etc/fstab.backup
       
 # Find your UUID:
sudo blkid -c /dev/null -o list

    
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

---

### Post by olivierhenry on 2014-03-09
Thank you very much for your help.
Problem solved.

---

