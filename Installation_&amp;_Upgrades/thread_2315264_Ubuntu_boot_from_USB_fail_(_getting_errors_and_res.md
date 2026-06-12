---
title: "Ubuntu boot from USB fail ( getting errors and restart )"
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by pxie on 2016-02-27
[COLOR=#111111][FONT=Ubuntu]Hi i made a bootable usb with ubuntu 14.04 ( first time i used rufus 2.7 then i tried to make it with Universal usb installer ) both provided the same result.[/FONT][/COLOR]

[LIST]
[*]Restarted pc and choosed to boot from that usb
[*]Selected - Try ubuntu without installing
[/LIST]
[COLOR=#111111][FONT=Ubuntu]After that it was spamming me errors then after a while it stopped screen switched to ubuntu loading screen and after a few seconds ( 20 - 30 ) it restarted . This happens again and again i managed to boot it from that usb 1 time from like 15 tries. Don't know what is wrong i will be helpful for every single advice. Thanks.[/FONT][/COLOR]

---

### Post by sudodus on 2016-02-27
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- Is Windows installed in the computer? In that case which version?

- Is the computer booting in UEFI mode or BIOS mode?

- Which colour is the screen where you select 'Try Ubuntu'? Dark red or black?

I could guess that you have problems with the graphics, but it will be easier to give advice, when we know more about your computer.

---

### Post by pxie on 2016-02-27
Hello. I have this laptop:

Lenovo IdeaPad y50-70 
Intel Core i7-4720HQ 2,60GHz
8gb RAM
nVdia gtx 980 4 gb also i have intel HD graphics 4600

Windows: 8.1

the color of screen is dark red.

Yes windows is installed because i use dual boot ubuntu / windows but today in the morning there was some kernel update i let it to install my notebook restarted during the instalation and could not mount so i decided to remove  the ubuntu and install it again or atleast boot it from usb but i have this strange problem. When my friend installed it for the first time i was having the same problem , when we choosed try ubuntu or install not sure now it  started spamming a lot of errors on the left side of screen ( errors were very similiar i could provide a screen if needed ) but we managed to boot it up and install it.

EDIT:
the error is spamming my screen and the left number 16.534303 is changing
[    16.534303] nouveau E[     PFIFO][0000:01:00,0] SCHED_ERROR [ UNK06 ]
...

---

### Post by sudodus on 2016-02-27
It often helps to use the boot option **nomodeset** with nvidia graphics. See this link (and links from it)

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

Do you know if there is [Nvidia Optimus](https://en.wikipedia.org/wiki/Nvidia_Optimus) graphics?

---

### Post by pxie on 2016-02-27
How to find out about Nvdia optimus graphic?

---

### Post by sudodus on 2016-02-27
I think it should be described in the manual of the computer, or there should be reported two graphics processors if there is optimus. I have no own experience of it, but  other people at these Ubuntu Forums know how to manage it.

If you don't know and can't find out easily, just try with the boot option nomodeset according to the link in post #4. I hope you get simple but working graphics, so that you can install proprietary nvidia graphics in the next step.

---

### Post by pxie on 2016-02-27
Could you please tell me how to disable acpi in grub? i tried to press e in grub menu but there was not any acpi= so i could not edit it

---

### Post by sudodus on 2016-02-27
Add **acpi=off** near the end of the line starting with linux. See the picture at

[Editing the GRUB 2 Menu During Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)

**ro quiet splash $vt_handoff** are boot options. Add your boot options near these options (or replace **quiet splash**). There should be a space between them.

---

### Post by pxie on 2016-02-27
linux /caspet/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

Tried to add acpi=off at the end of the line = the same result errors , when i replaced quiet splash with acpi=off or put it near those options and pressed ctrl+x it gave me black screen and nothing happened i had to manually put off laptop.

---

### Post by sudodus on 2016-02-27
That was not the right option for your computer. Try **nomodeset** and some other boot options!

If you put it before the dashes, **... nomodeset --**, it will be used in the live session. If you put it after the dashes, **... -- nomodeset**, it will be transferred to the system to be installed. This is in the new versions (the syntax was changed maybe one year ago).

---

### Post by pxie on 2016-02-27
I tried them but did not work , now i replaced 2 times quiet splash with nomodeset and both times it booted up linux i do not know if it was by luck because sometimes i can boot it with quiet splash or it actually helped and solved my problem but anyway thank you for a help. Btw i have one question for you "[COLOR=#000000]That was not the right option for your computer" what did u mean by that can i damage computer somehow by that?[/COLOR]

---

### Post by sudodus on 2016-02-27
No advanced thinking behind it: It did not work, so it was not the right option.

I have only bricked one graphics card, and it was many years ago. I was using DSL (damn small linux) and booted it in a very special way. I have not managed to damage any hardware with a boot option. But it might be possible, so if things do not work, you should turn off the computer rather soon (of course you must wait long enough to give it a chance to get ready).

Instead of hard shutdown (pressing the button for several seconds), you can use this System Request sequence to reboot

***SysRq r e i s u b***

and the following one to shut down (o for off)

***SysRq r e i s u o***

Often you get SysRq by pressing the ***alt + PrtScr*** keys. Keep them pressed while slowly pressing the other keys one after another (r e i s u b)

---

### Post by pxie on 2016-02-27
Actually when i replace quiet splash with nomodeset it boots fine ( except it boots differently = i dont see red screen ubuntu anymore just some operations going through and then ubuntu desktop poops out ). Now when i finally can boot up the ubuntu im going to install it ( make dual boot with windows ) but how to set nomodeset globally? I mean when the ubuntu will be installed everytime i need to press E in grub and replace "quiet splash" or?

---

### Post by sudodus on 2016-02-27
I described that in post #10 (during installation). After installation you can do it according to this link

[Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

the paragraphs about

> GRUB_CMDLINE_LINUX

    Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
        To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

Edit the file **/etc/default/grub** and ***update grub***. It is described in the link.

---

### Post by pxie on 2016-02-27
Thank you a lot for the help.

---

