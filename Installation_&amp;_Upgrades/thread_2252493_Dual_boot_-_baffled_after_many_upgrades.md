---
title: "Dual boot - baffled after many upgrades"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by kennedyhart716_a on 2014-11-12
I've been updating Ubuntu for several years now without problems. I've upgraded from ubuntu 13.10 to 14.04 via live CD on a dual boot desktop alongside Win 7. I was offered several options including upgrading keeping files etc. Chose this and all seemed to go well. Now the machine would only go directly to Windows without the boot options. I tried a fresh install from disk and was given option of removing 14.04 with fresh install. Chose this - I have data backup. Same result - directly into Windows, and no dual boot menu. 
Any guidance [not too technical, please] would be appreciated.

Ken

---

### Post by yancek on 2014-11-12
Is your windows installed in MBR mode or EFI?  I would expect MBR.  Were you previously using the Ubuntu Grub bootloader to boot windows and your earlier versions of Ubuntu?  Did you select to install the Grub bootloader to the master boot record, /dev/sda if you have only one hard drive?

---

### Post by kennedyhart716_a on 2014-11-12
Thanks for replying. EFI? Sorry, win 7 was loaded on a normal installation. I don't understand what this acronym stands for.  The bootloader always came up with ubuntu at the top followed by windows as expected. On previous versions the upgrade happened automatically. I've never had to select to install the b/l to the master boot record [yes ubu and win are on one drive] since first installation back about end of 08.

---

### Post by yancek on 2014-11-12
The default installation usually install to the master boot record so I'm not sure what happened.  I've never used the option you selected so I don't know what one would expect.  You do not see an option for Ubuntu, correct?  Use the Ubuntu DVD and go to the site below which explains how to reinstall Grub on Ubuntu.  If that doesn't work, post back.  The boot repair tool might be the simplest option.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by kennedyhart716_a on 2014-12-02
Hello Yancek if you're still checking this thread. Was unwell for time, then unavailable for few days, so couldn't reply to your post. I followed the link, but couldn't work out which of the options was relevant. Took the suggested link to the Boot-Repair community and found the following for using live CD to load Boot-Repair. Instructions as follows:
Start from Live CD - Go to Terminal. Enter the following:
    [B] sudo add-apt-repository ppa: yannubuntu/boot repair [Enter]
     sudo apt-get update [Enter]
     sudo apt-get install -y boot-repair && (boot-repair &) [Enter][/B]
Then to enter Boot Repair and choose first option.
I have no idea if this works as the first line brought up an error message saying that only one name could be entered [think that was the phrase]. Tried various combinations of the part following **ppa:** but with the same result. 
I think that part of the trouble is that I get confused with the terminology of options offered, so I may have even followed the wrong avenue.
Please can you advise further. *By the way, answering your question, I not only see no option for Ubuntu, the computer just loads straight into Win 7 without a menu.* Also, 14.04 loaded on to my laptop, which has Vista, with no problem - menu as well.

---

### Post by kennedyhart716_a on 2014-12-03
Is there anyone who can help me out, please? Otherwise I will be condemned to a Windows only option, with a 14.04 program alongside just waiting to be accessed.

---

### Post by Mark Phelps on 2014-12-04
I've personally had problems with boot-repair so all I can recommend it the material in the link which shows how to reinstall GRUB:  [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by yancek on 2014-12-04
I  have seen numerous posts here explaining and people seem to have success with it.  I can't give you any input on it as I've never used it.  If you want to use the link I posted previously, go to the page and scroll about half way down the page to 'via the LiveCD terminal' where it has pretty explicit instructions.  Did you select the option to get the output of the script boot repair runs to gather information when you use it?  I know it's there but again, I haven't used it.  Found a link below which explains, select to Create a Bootinfo summary.  You can post that here and it should help someone to help you. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[h=3][/h]

---

### Post by mastablasta on 2014-12-05
> **kennedyhart716_a said:**
> Is there anyone who can help me out, please? Otherwise I will be condemned to a Windows only option, with a 14.04 program alongside just waiting to be accessed.

it should be 

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
not boot repair

or you can use as advised a boot repair disk or manually update grub (I mean update it using command line)


provided all went well the menu entry should reappear. 

I am not sure why it would disappear, unless you did some windows boot recovery. Edit: or maybe certain updates rewrite the master boot record (MBR) with windows boot manager that does not recognise anything else but windows.

---

