---
title: "Grub Rescue Help!"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by princetrey12 on 2011-08-24
My laptop came with Windows 7 on it and a while back I dual installed Ubuntu on it. A few days ok I was looking for some more space and accidentally deleted my Ubuntu partition. Now when I boot up all I get is grub rescue. I've tried reinstalling Ubuntu but whenever I click to install or try Ubuntu it eventually ends up with an "initramfs" prompt. Any help is greatly appreciated as I'm going crazy right now trying to figure this out.

---

### Post by YesWeCan on 2011-08-24
To boot Windows again you will need to restore the MBR boot code. You can do this using a Windows install CD and selecting repair or by booting a Ubuntu live CD and running:
sudo fdisk -l
to check the name of your disk drive; I'll assume it is sda
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If this doesn't get Windows booting you'll need to download and post the output of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) (inside code tags...highlight the text and click #)

---

### Post by princetrey12 on 2011-08-24
I can't boot into Ubuntu at all. And I currently don't have a copy of my repair disks for windows.

---

### Post by YannBuntu on 2011-08-25
Hello

AFAIK Lilo cannot repare a MBR Seven or Vista, only XP. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") can. 

Boot-Repair also proposes a way to create a Boot-Info summary, which is much easier than the "manual" one: [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980) :guitar:

---

### Post by YesWeCan on 2011-08-25
> **YannBuntu said:**
> AFAIK Lilo cannot repare a MBR Seven or Vista, only XP. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") can. 
Lilo will work fine. Do you understand how MBR code works?

---

### Post by Blasphemist on 2011-08-25
It seems to me that maybe we ought to get back to the real request here. Remember that the ubuntu parition got accidentally deleted apparently. I see no logic in getting involved with lilo since it wasn't being used and is used by so few anymore. And just getting the windows boot back seems like an incomplete solution most likely.

What I read of this request says that the ubuntu live cd boots but when either install or try is selected, the initramfs prompt is the result. So that hoses using boot-repair Yann and also your commands yeswecan. Right now the OP says the grub-rescue or initramfs prompts are all that is available. 

Let's start with what you were doing and how did you delete the partition? Were you using wubi for ubuntu? Do you have RAID? What cd or usb are you trying to boot to when you get the initramfs prompt? Does it work on another pc since you must be using another to get to this forum?

You may want to try this cd. [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) There are tools on it for recovery of the deleted partition. You may want to start there.

---

### Post by princetrey12 on 2011-08-25
I don't have another computer to test it on, im doing this through my phone. 
 
But I had several partitions on my harddrive(one I was using to store music)I was trying to delete the partition but accidentally deleted the Ubuntu partition. I had 10.10 installed and upgraded to 11.04(this was before the deletion)I don't really care about Ubuntu I just need to get back into Windows 7, im in college and alot of my stuff is saved there. The only thing I have at my disposal right now is a flashdrive that has Ubuntu on it. I could try it on my room mates laptop later and will update with the results. But if there is anyway I can repair Windows 7 MBR using a flashdrive I would love to k ow.

---

### Post by J_Boi on 2011-08-25
Not trying to hijack this thread but I have a similar problem and I felt it was not needed to create another thread.

I am guessing that I have also screwed up my MBR.

I was originally running Windows 7 64 bit. I then decided to try to install Ubuntu 11.04 alongside of Windows using my external HDD. I installed Ubuntu and am able to boot into it find but at the Grub menu when I select the Windows option it doesn't do anything. I press enter the screen flashes and the Grub screen returns. 

Ubuntu boots fine. I just need to be able to boot back into Windows. I was reading YannBuntu's post on Boot-repair-disk. Not sure if that will help.

---

### Post by bcbc on 2011-08-25
> **YesWeCan said:**
> To boot Windows again you will need to restore the MBR boot code. You can do this using a Windows install CD and selecting repair or by booting a Ubuntu live CD and running:
sudo fdisk -l
to check the name of your disk drive; I'll assume it is sda
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If this doesn't get Windows booting you'll need to download and post the output of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) (inside code tags...highlight the text and click #)
+1

> **princetrey12 said:**
> I don't have another computer to test it on, im doing this through my phone. 
 
But I had several partitions on my harddrive(one I was using to store music)I was trying to delete the partition but accidentally deleted the Ubuntu partition. I had 10.10 installed and upgraded to 11.04(this was before the deletion)I don't really care about Ubuntu I just need to get back into Windows 7, im in college and alot of my stuff is saved there. The only thing I have at my disposal right now is a flashdrive that has Ubuntu on it. I could try it on my room mates laptop later and will update with the results. But if there is anyway I can repair Windows 7 MBR using a flashdrive I would love to k ow.

Just do what *YesWeCan* suggested. Boot from the Ubuntu USB, select "Try it" (without installing) and then install lilo and write it to the member as suggested. This will get windows booting again.

PS you can also 'undelete' partitions fairly easily using testdisk.

---

### Post by YannBuntu on 2011-08-26
> Lilo will work fine.

"may" work fine. I have seen several cases on ubuntu-fr forum where Lilo did not work, the users had to use a Rescue disk after to repair damages.
And also Boot-Repair is easier to use, it does the job in 1 click.

[IMG]http://pix.toile-libre.org/upload/img/1312989003.png[/IMG]

> Do you understand how MBR code works?

???
Agressivity is useless. We are here to help people.

---

### Post by YesWeCan on 2011-08-26
[QUOTE=YannBuntu]
AFAIK Lilo cannot repare a MBR Seven or Vista, only XP. Boot-Repair can.[/quote]
[QUOTE=YannBuntu]???
Agressivity is useless. We are here to help people.[/QUOTE]
Your original statement is not right. I think in your enthusiasm to advocate your boot-repair program you have cast aspersions on Lilo which is a long-established program and installs proper MBR boot code. People should be aware of this tool. If you do not understand what Lilo does I will be happy to explain it.

> "may" work fine. I have seen several cases on ubuntu-fr forum where Lilo did not work, the users had to use a Rescue disk after to repair damages.
And also Boot-Repair is easier to use, it does the job in 1 click.
You are probably talking about other problems than the MBR, such as a corruption of the Windows partition boot record or NTLDR or BOOTMGR or the embedded bootstrap code.
If you have an example of when Lilo did not install proper MBR boot code I would like to see it.

---

### Post by princetrey12 on 2011-08-26
I can NOT boot into windows 7 or ubuntu(trial or installation)at all.

---

### Post by Hakunka-Matata on 2011-08-26
> **princetrey12 said:**
> I can NOT boot into windows 7 or ubuntu(trial or installation)at all.

OK, I believe you, but please relate what happens when you try to boot into the ubuntu liveCD?  Or maybe you do not have a liveCD handy?

---

### Post by YannBuntu on 2011-08-27
@YesWeCan: you are right, my judgment on Lilo may have been falsed by problems other than MBR. Sorry for that. In case I see another case like this, i'll try to get data before the rescue cd is used and i'll do bug report. But i'll have to search on this forum because on ubuntu-fr's nobody uses Lilo any more.
By the way, i saw you help a lot on this forum so thank you for this, and sorry if i misunderstood the tone of your previous message.

@princetrey : please try SuperGrubDisk just in case.

---

### Post by princetrey12 on 2011-08-28
I solved my own problem so this thread can be closed now

---

### Post by Hakunka-Matata on 2011-08-28
[B]princetrey12:
  
[/B][LEFT]Please share your solution, spread the knowledge :)  To mark this thread [SOLVED], use [COLOR=Red]_**Thread Tools **_[/COLOR]upper right hand side.  You must do it, we are not allowed to change the status.[/LEFT]

---

### Post by princetrey12 on 2011-08-28
I just repaired the MBR using a windows 7 repair disc.

---

### Post by Hakunka-Matata on 2011-08-28
Hey, that's great, glad you are back in business.  Thanks for telling us what did it.

---

