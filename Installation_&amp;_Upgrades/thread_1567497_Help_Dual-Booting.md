---
title: "Help Dual-Booting"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by MasterTHC on 2010-09-03
I have Ubuntu 10.04 LTS installed first then I the 10.04 Live CD to use GParted to resize the partiton so i install Win7 and make the free space into ntfs but each time i do this it just closes and restarts and runs Ubuntu disk checker and i keep coming back to the login screen 


here some screenshots
[IMG]http://i55.tinypic.com/2ufd8qt.png[/IMG]
[IMG]http://i55.tinypic.com/nmi749.png[/IMG]

---

### Post by wilee-nilee on 2010-09-03
You need to right click on the swap and turn it off.

You also have your extended around the swap and not Ubuntu, and the swap, not a big deal but usually the Ubuntu would be inside.

Also don't run both of those commands together shrink the partition then build the ntfs.

---

### Post by MasterTHC on 2010-09-03
> **wilee-nilee said:**
> You need to right click on the swap and turn it off.

You also have your extended around the swap and not Ubuntu, and the swap, not a big deal but usually the Ubuntu would be inside.

Also don't run both of those commands together shrink the partition then build the ntfs.

I'm going to try this will post results

---

### Post by wilee-nilee on 2010-09-03
> **MasterTHC said:**
> I'm going to try this will post results

If all goes well and you get W7 installed you will need to reload the grub2 bootloader to the MBR, to have a choice of Ubuntu or W7.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by MasterTHC on 2010-09-03
> **wilee-nilee said:**
> If all goes well and you get W7 installed you will need to reload the grub2 bootloader to the MBR, to have a choice of Ubuntu or W7.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Unfortunately all didn't go well can you if me step by step instructions on how to make the partitons so that i have a good dual-boot because it keeps crashing and overheating when i turned off swap and resized the ubuntu. My Live CD is 10.04 LTS Desktop Edition

---

### Post by wilee-nilee on 2010-09-03
So how attached are you to the Ubuntu install you have now. Generally people install W7 or any MS first then Ubuntu.

Looking at your gparted shots if the swap is off then the keys in the partition line should not be showing.
[ATTACH]168424[/ATTACH]

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> So how attached are you to the Ubuntu install you have now. Generally people install W7 or any MS first then Ubuntu.

Looking at your gparted shots if the swap is off then the keys in the partition line should not be showing.
[ATTACH]168424[/ATTACH]

Ok i turned swap off and did partitioned the thing and installed Win7 now i'm going to restore Gurb

---

### Post by wilee-nilee on 2010-09-04
If you have any problems let us know.

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> If you have any problems let us know.

I have a problem with restoring GRUB i tried your link
```
https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD
```
I tried the first and second one but keeps booting into Ubuntu or it's goes into grub-rescue

---

### Post by dirghrabadia on 2010-09-04
As wilee-nilee said, it generally preferred to install W7, restart, then boot using Gparted, make the desired space for Lucid (as W7 tends to occupy the entire hard drive), and then boot using Live CD and get started with Lucid installation.

---

### Post by wilee-nilee on 2010-09-04
> **MasterTHC said:**
> I have a problem with restoring GRUB i tried your link
```
https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD
```
I tried the first and second one but keeps booting into Ubuntu or it's goes into grub-rescue

First have you run in the installed Ubuntu terminal,
```
sudo update-grub
```
If this doesn't get it working correctly post the bootscript in my signature, in code tags this will give us much more information.

Trading bootloaders in the MBR is no big deal.

---

### Post by MasterTHC on 2010-09-04
Well i have my home theatre on ubuntu so making win7 format everything is kinda pointless i'm going to try the copying grub form the live cd again

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> First have you run in the installed Ubuntu terminal,
```
sudo update-grub
```If this doesn't get it working correctly post the bootscript in my signature, in code tags this will give us much more information.

Trading bootloaders in the MBR is no big deal.

it's asking for sudo password and my login pass doesn't work on it

---

### Post by wilee-nilee on 2010-09-04
> **MasterTHC said:**
> it's asking for sudo password and my login pass doesn't work on it

When, where, what is?

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> When, where, what is?
It's asking for sudo pass on the installed ubuntu
[IMG]http://i51.tinypic.com/16bn15k.png[/IMG]

---

### Post by wilee-nilee on 2010-09-04
That is a problem when did your password stop working? I assume you are aware that the password doesn't show in the terminal window when typed.

So you login; no auto-login, correct, and your password wont work in the terminal.

---

### Post by wilee-nilee on 2010-09-04
So let me add this here is a link for troubleshooting the sudo problem.
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
So you can view but not edit the files suggested in this first link in the terminal.
```
cat /etc/sudoers
```
And 
```
cat /etc/group
```

From the same site how to change your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You will notice that the actual editing is from using the recovery line in the grub boot prompt. When you turn the computer on if you press on the shift immediately and several times until grub shows you will see the recovery.

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> That is a problem when did your password stop working? I assume you are aware that the password doesn't show in the terminal window when typed.

So you login; no auto-login, correct, and your password wont work in the terminal.

I turn my laptop on i login manually and when i go to terminal I type 
```
sudo update-grub
``` 
and it asks for sudo password but wherever i attempt to type something it says wrong pass

---

### Post by wilee-nilee on 2010-09-04
> **MasterTHC said:**
> I turn my laptop on i login manually and when i go to terminal I type 
```
sudo update-grub
``` 
and it asks for sudo password but wherever i attempt to type something it says wrong pass

I am not real familiar with why this would happen, or what you have or haven't done that may be associated as far as user or group permissions. All I can do is say take a look at the links, worse case scenario since the partition has only 10 gigs you could do a reinstall.

---

### Post by MasterTHC on 2010-09-04
> **wilee-nilee said:**
> I am not real familiar with why this would happen, or what you have or haven't done that may be associated as far as user or group permissions. All I can do is say take a look at the links, worse case scenario since the partition has only 10 gigs you could do a reinstall.

Since i have a windows cd also isn't it easier to install windows first then ubuntu if that's true how can i delete the ubuntu

---

### Post by wilee-nilee on 2010-09-04
> **MasterTHC said:**
> Since i have a windows cd also isn't it easier to install windows first then ubuntu if that's true how can i delete the ubuntu

This thread has accomplished little, I think maybe a little reading might help you to understand.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

