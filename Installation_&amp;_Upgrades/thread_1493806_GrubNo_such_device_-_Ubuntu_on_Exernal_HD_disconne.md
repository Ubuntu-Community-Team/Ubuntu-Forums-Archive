---
title: "Grub:No such device - Ubuntu on Exernal HD disconnected"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by il_Wentu on 2010-05-26
Hi all

I have a problem similar to this
[http://ubuntuforums.org/showthread.php?t=1318540](http://ubuntuforums.org/showthread.php?t=1318540)
but the thread didn't help me very much.
What I need is Ubuntu installed on an external HD so that when the HD is connected to my (Vista home basic) notebook i can choose between Ubuntu 10.04 and Vista but when the HD is not connected to the notebook, i can still choose Vista (it is ok if, in this latter case, choosing ubuntu will lead to an error).

The first part is OK, when the HD is connected everything goes fine. 
When the HD is disconnected, i receive an error during boot: No Such Device, followed by a UID. I then have the grub rescue> prompt.

It's strange but the prompt doesn't seem to recognize any command (exit, ls or the other simple commands among those supported by grub rescue).

Is there a way to fix this, maybe working on the grub.cfg file ?

thank you very much

Wentu

---

### Post by presence1960 on 2010-05-26
You probably have GRUB installed on the MBR of the internal drive. GRUB looks to files on your Ubuntu partition to boot so when the external is diconnected the process can not complete. What you need to do is put GRUB on the MBR of the external disk and restore the windows bootloader to MBR of the internal. Should be a simple fix...but to be sure I need precise info. Do this with your external plugged in:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by darkod on 2010-05-26
I think your problem is slightly different. When you were installing ubuntu you should have checked where the grub2 bootloader will go. It seems it installed on the MBR of the internal hdd. So with the ext hdd disconnected, it doesn't have its config files and the error is there.

You would need to install a windows MBR on the int hdd, and grub2 on the ext hdd for what you want to achieve.

If you run this script and post the content of the results file, we will know for sure what is going on:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by darkod on 2010-05-26
> **presence1960 said:**
> 

Hey, look who's here. :)

---

### Post by presence1960 on 2010-05-26
> **darkod said:**
> Hey, look who's here. :)

Hey Darko. Good to "see"you. I have been very busy with work and my daughter has been busy training in Tae Kwon Do. She entered an international mixed martial arts tournament and finished second in sparring and third in weapons. I haven't had a lot of free time so haven't been on as much for about a month or two. It is good to be back. How you been?

---

### Post by darkod on 2010-05-26
> **presence1960 said:**
> Hey Darko. Good to "see"you. I have been very busy with work and my daughter has been busy training in Tae Kwon Do. She entered an international mixed martial arts tournament and finished second in sparring and third in weapons. I haven't had a lot of free time so haven't been on as much for about a month or two. It is good to be back. How you been?

Me too. I was moving to Spain (well, still trying to make it a permanent move in fact) and had to wait 6 weeks for ADSL. :) So I've been missing too.

---

### Post by presence1960 on 2010-05-26
> **darkod said:**
> Me too. I was moving to Spain (well, still trying to make it a permanent move in fact) and had to wait 6 weeks for ADSL. :) So I've been missing too.

Hope it works out for you and good wishes in your hopefully permanent new home.

---

### Post by Arand on 2010-05-26
1. Reinstate the windows mbr by either using bootrec.exe from a recovery CD, or something like EasyBCD (propably the easier choice if you can still boot win)

2. Boot an Ubuntu LiveCD and install grub to the mbr of your usb HD
Something along the lines of:```
mount /dev/sdY# /mnt
grub-install --root-directory=/mnt /dev/sdY
```Here Y is the letter of the usb HD (maybe "b"), # is the number of the ubuntu partition (maybe "1").

3. Make sure your bios is set to boot from the usb HD before the primary HD.

*. Result is that when usb disk is not connected, only the windows bootloader will be used, and when the usb disk is connected, grub will be loaded from the usb disk and present the choices.

Other solutions would be to let BCD chainload grub, or keep grub files on the NTFS partitions, both I feel more complicated, and possibly problematic.

...

Um people? I though we had a topic?

Isn't this bootinfo script getting a bit out of hand? The solution is pretty obvious without messing about with the script, right? 

- Arand

---

### Post by darkod on 2010-05-26
> **Arand said:**
> 
Um people? I though we had a topic?

We're just killing time until the OP replies. :) You had to ruin the party... :(

> 
Isn't this bootinfo script getting a bit out of hand? The solution is pretty obvious without messing about with the script, right? 

- Arand

In most cases this is true, but sometimes there are situations you can't predict so specifying commands "blind" can hit you back. :)

---

### Post by presence1960 on 2010-05-26
> Isn't this bootinfo script getting a bit out of hand? The solution is pretty obvious without messing about with the script, right?


I refuse to try to help anyone with booting problems without seeing their info from the script. The reason is very simple: a lot of times what users report their setup is and what is actually on their machines are not the same. I refuse to blindly give commands when I can have the whole setup and boot process in front of me in black and white. Then I can give precise commands to run in terminal. Although I understand the nomenclature sdXY someone else may not or may put the wrong characters in for XY and install GRUB to the wrong place or mount the wrong partition. In case you haven't been around here for a while you will see the boot info script is a very useful tool not only for troubleshooting but for newer people to learn about their setup and boot process and how it all works through studying the info in the results of their script.

---

