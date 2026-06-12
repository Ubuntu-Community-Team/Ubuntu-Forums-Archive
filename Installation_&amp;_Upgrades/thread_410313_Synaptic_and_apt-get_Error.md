---
title: "Synaptic and apt-get Error"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by J_E_S_T_E_R4 on 2007-04-15
Mmkay... I've got myself a bit of a problem. Every time I try to install a package through Synaptic or through the terminal using apt-get, I get an error message. The terminal gives me: 

jordan@beige:~$ sudo apt-get -f install
Password:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

And Synaptic gives me this in an error dialog when I try to open it.

E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

Wonderful, eh?

Also, the GDebi Package Installer crashes when I try to install a package that I already have on my computer. Synaptic will crash when I click the 'Reload' button, and after it has downloaded the files.

I doubt it's HD space issues, there's a little less than a gig free. (it's only a 6gig drive to start with.)

Thank you.



[EDIT] So I just realised something... I didn't have this problem until I tried to install something.
This was the file: [http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654](http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654)

Should have known not to trust anything made by the Army, eh?

---

### Post by JLB on 2007-04-15
try an apt-cache clean and see if that helps. ```
sudo apt-cache clean
```

then re-run the repos update and try it again.

---

### Post by J_E_S_T_E_R4 on 2007-04-15
jordan@beige:~$ sudo apt-cache clean
Password:
E: Read error - read (5 Input/output error)

---

### Post by zvacet on 2007-04-16
Run** df** in terminal to see if it is any free space left.

---

### Post by J_E_S_T_E_R4 on 2007-04-16
jordan@beige:~$ df
Filesystem     1K-blocks    Used              Available     Use%    Mounted on
/dev/hdb1      6086432      5379400      645184        90%      /
varrun             258024        132                257892        1%        /var/run
varlock	           258024        4                    258020        1%         /var/lock
procbususb   10240          128                10112           2%        /proc/bus/usb
udev               10240           128               10112           2%        /dev
devshm          258024        0                    258024        0%        /dev/shm
lrm                  258024         18132	   239892         8%       /lib/modules/2.6.17-11-386/volatile

EDIT:  Bloody.... This table refuses to work right.

---

### Post by J_E_S_T_E_R4 on 2007-04-28
w00t! Problem solved!

If anyone ever comes across something like this again:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by midnight286 on 2007-12-18
I have the same problem but I couldn't figure out how the link this user points to is going to help.    It seems as if I'm running two different versions of APTtoCD.  Could this pose the problem?

---

### Post by J_E_S_T_E_R4 on 2007-12-31
In my case, if I remember right, it was a problem with /etc/apt/sources.list_backup itself. It's been a while, but if I'm not mistaken, the program that I tried to install had tried to replace that file with its own source list, or had deleted it entirely. By following that link, I was able to replace the missing file, and everything is working all nice and pretty now.

---

