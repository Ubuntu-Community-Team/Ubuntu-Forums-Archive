---
title: "Freeze at installation %95"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by psychetron on 2009-11-27
when i tried to install ubuntu 9.04 it freezes at 

"installing language packages
preparing to configure lupin-support %95"

i had previously installed this version of ubuntu on my laptop. but then a problem occurred and it can't be opened after login screen. so i removed it from add/remove section of windows xp and tried to reinstall it but it freezed at installation at the same step above. i thought that the uninstallation of ubuntu was not right and it can't be installed again now. so i made a complete format containing windows and then i can install the ubuntu. but then again ubuntu can't be opened after i tried to install my modem. so i did this complete format again. but now again ubuntu can't be installed. it freezes at %95. what can be the solution please? i really got nerved. i've made 5-6 formats in 3 days and the result is nothing. i'm trying to install wubi.

what can be the reason for not installing even though i made a complete format? i reinstall all things and it previously worked for installation but now it doesn't.

---

### Post by Subbu_09 on 2009-11-27
> **psychetron said:**
> when i tried to install ubuntu 9.04 it freezes at 
 
"installing language packages
preparing to configure lupin-support %95"
 
i had previously installed this version of ubuntu on my laptop. but then a problem occurred and it can't be opened after login screen. so i removed it from add/remove section of windows xp and tried to reinstall it but it freezed at installation at the same step above. i thought that the uninstallation of ubuntu was not right and it can't be installed again now. so i made a complete format containing windows and then i can install the ubuntu. but then again ubuntu can't be opened after i tried to install my modem. so i did this complete format again. but now again ubuntu can't be installed. it freezes at %95. what can be the solution please? i really got nerved. i've made 5-6 formats in 3 days and the result is nothing. i'm trying to install wubi.
 
what can be the reason for not installing even though i made a complete format? i reinstall all things and it previously worked for installation but now it doesn't.
 
Based on the suggestions I have seen in this form, I can suggest a couple of them.
Please try and see if it can solve the issue for you.
 
1. Try to get a different installation LIVE CD and see if it works to fix the issue.
 
2.First get your Windows XP installed and working fine in the formatted C drive. Then, free-up any one of the drives and dedicate it fully for Ubuntu. Like one of the D / E or F drives should be fully dedicated for it with no data or programs in it. There is a suggestion to delete the drive you have identified for Ubuntu from the disk management utilitly in Windows XP and to make it an unpartitioned space. Then, boot
into your LIVE CD, select install UBUNTU and then select manual paritioning. At this
point your unpartiioned (that is the dedicated drive space you alloted for Ubuntu)
should be found by Ubuntu and use it for your installation. After the instalaltion completes successfully, you should see a boot option for Win X and Ubuntu.
 
Hope this may solve your problem.
 
Cheers.
any

---

### Post by phillw on 2009-11-27
+1 ... The rules of CD's to stop 'funnies' are ...

1) md5 check the iso file [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) Burn at 4X speed (or lower) - If you can't burn that slow then --> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) md5 check the cd, as per step 1.

As subuu will testify, a 'bad' cd is a nightmare.

when slicing disks - XP is prone to squealing like a scalded pig. Once you have sliced you disk - Let XP settle down - it often wants to do file-checks etc. Don't put Ubuntu on untill the XP area is happy.

Hope the above helps you. The getting of the image etc is covered here --> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Regards,

Phill.

---

### Post by psychetron on 2009-11-27
i don't use a cd when installing. i use daemon tool to open the iso file. and by that way i could install it once. so i don't think it is about preparing a cd that is written with low speed or other things or it can really be about cd issue?

---

### Post by Subbu_09 on 2009-11-27
> **psychetron said:**
> i don't use a cd when installing. i use daemon tool to open the iso file. and by that way i could install it once. so i don't think it is about preparing a cd that is written with low speed or other things or it can really be about cd issue?
 
Hi,
 
If it is done using a daemon tool, then you are adding another possibility for things to go wrong in the installation. We should always follow the standard, tested and tried methods for these kind of dual boots and additional installation on a Windows machine.
Also, as I have found in my case, CD's can definitely be a nightmare until you are lucky and have a very good CD-ROM media and a CD-RW drive. So, please try the options given here and let us know the results. It may easily solve your problem. If not, you can get help from others on different options.
 
Good luck.

---

### Post by psychetron on 2009-11-27
> **phillw said:**
> +1 ... The rules of CD's to stop 'funnies' are ...

1) md5 check the iso file [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) Burn at 4X speed (or lower) - If you can't burn that slow then --> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) md5 check the cd, as per step 1.



ok. i will write the iso into cd and give it a try. but here i did the first step. md5 check the iso file and it returned "MD5 check sums are different". so writing this iso file to a cd and trying to install with it is useless or not?

---

### Post by psychetron on 2009-11-27
> **psychetron said:**
> ok. i will write the iso into cd and give it a try. but here i did the first step. md5 check the iso file and it returned "MD5 check sums are different". so writing this iso file to a cd and trying to install with it is useless or not?

ok. md5 check is done. they are the same. i will try to wirte onto cd and install.

---

### Post by psychetron on 2009-11-28
after writing it to a cd i can hardly install it. because it can't be read from cd for several times. before installing it i formatted partition F: that is about 35 gbs. and when i tried to install, in choosing part step i cannot choose F:. i cannot choose any suitable part. there seems to be 992 mb of free space but there is absolutely more. anyway i installed it over windows and now i got just ubuntu on the laptop. i was ready for that (writing over windows) but i really gone mad about this installation thing and go on.  actually i want to use both of them on my computer. now i got only ubuntu installed and can i do anything for that dual boot issue. why couldn't i choose the free space at installation. there was option for manually choosing the space but again it didn't work.

and there is another thing that the screen got darkened when i installed ubuntu. i could hardly see the screen and the hotkey for screen resolution don't work. but for example the hotkey for volume works. is there any solution for this darkened screen.

---

### Post by phillw on 2009-11-28
So, let me get this right. You have installed Ubuntu 9.10 Over your XP install ?

can you post the response to 

```
sudo fdisk -l
```

and 
```
df -ha
```

thanks,

Phill.

---

