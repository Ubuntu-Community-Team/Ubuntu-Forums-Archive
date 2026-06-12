---
title: "Nvidia driver issue on fresh hardy x64 install"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by matre on 2008-06-10
Hi,

I have a fresh hardy x64 install which I have updated with the latest updates including kernel 2.6.24-18.  I then installed the latest NVIDIA driver (I have a 9600GT so restricted driver manager is not a option).  Steps I followed were
1. Installed build-essentials
2. Drop out to console using CTRL-ALT-F1
3. stop GDM with sudo /etc/init.d/gdm stop
4. sudo ./NVIDIA-Linux-x86_64-173.14.05-pkg2.run
5. Followed all the prompts answering yes to everything.
6. Right at the end I get the warning "WARNING: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.173.14.05'); assuming successful installation.".  
7. Doesnt seem to be a show stopper so restart X with sudo /etc/init.d/gdm start.
8. Starts fine and I then update sudo gedit /etc/default/linux-restricted-modules-common with DISABLED_MODULES="nv"
9. Restarted machine for good measure.

So things look good, NVIDIA screen flashes by, login fine and all looking good.  But now certain apps are behaving strangely.  Office writer locks up and then crashes.  Office spreadsheet window goes grey and crashes.  Some apps take ages to start such as Amorok...  

I am making the uneducated guess that the NVIDIA driver is the cause as they were all fine before I installed the driver and nothing else has changed.  Any thoughts?

Thanks in advance,

Matt

---

### Post by matre on 2008-06-10
I searched long and hard before posting and still managed to miss this thread.  

[http://ubuntuforums.org/showthread.php?t=819210]("http://ubuntuforums.org/showthread.php?t=819210")

Will try tonight when I get home from work.  I missed alot of threads in both x64 and Multimedia sections it seems.  Note to self, learn how to better use the search function!

Matt

---

### Post by matre on 2008-06-11
Havent fixed my issue yet but have some progress...

libGL.so.1 error can be fixed by installing ia32-libs however this doesnt fix my issue.  

I actually think the NVIDIA driver is working fine so my title is probably wrong now.  But openoffice crashes consistently and it is someway related to the NVIDIA driver as it didnt happen before I installed the driver..  There is nothing in the syslog when openoffice crashes.  Office Writer for example starts up but then just locks after which the windows fades to grey and few seconds later and then asks me to force quit.  Spreadsheet and presentation crash as well although I tend to get some interaction and functionality before this happens.
    

I see references to an issue related NVIDIA, compiz and openoffice causing crashes and lock up here and there which seems to be my issue.  I saw references to animations causing issues so I turned that off in compiz setting but that didnt seem to help.  


Has anyone had a issue like this?  Any ideas?  

Thanks in advance,

Matt

---

### Post by tenmoi on 2008-06-11
It could be that openoffice gets corrupted somehow. I suggest doing remove -- purge it and reinstalling to see if this helps.

I never have that libGL.so.1 problem. It only happens when I uninstall the NVidia driver but that does not matter.

---

### Post by matre on 2008-06-11
I agree.  

My issue looks suspiciously like this (although I havent seen that stack trace) [http://ubuntuforums.org/showthread.php?t=822052]("http://ubuntuforums.org/showthread.php?t=822052").

This references a known bug is[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676") which has a workaround I will try tonight after work.

Matt

---

### Post by tenmoi on 2008-06-11
I have just enabled compizfusion and opened openoffice. Things are running fine. I think you should enable the proposed update and update your system. Maybe it will solve your problem.

---

### Post by matre on 2008-06-12
My problem is this bug [https://bugs.launchpad.net/ubuntu/+s...64/+bug/236676]("https://bugs.launchpad.net/ubuntu/+s...64/+bug/236676").

I removed openoffice.org-gnome and openoffice.org-gtk, deleted the .openoffice.org2 directory from my home directory and restarted for good measure and the lockup seems to be gone.  Only downside is back to default openoffice look and feel but that isnt the end of the world.

Matt

---

