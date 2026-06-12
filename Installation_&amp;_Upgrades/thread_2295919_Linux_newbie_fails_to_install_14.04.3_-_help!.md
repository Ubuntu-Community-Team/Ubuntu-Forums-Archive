---
title: "Linux newbie fails to install 14.04.3 - help!"
date: 2015-09-22
forum: Installation &amp; Upgrades
---

### Post by Wraenna on 2015-09-22
I have an old Toshiba Satellite A60 laptop which runs on Windows XP. I thought it would be a neat idea to switch it to Ubuntu, so I downloaded 14.04.3 (the 32-bit version) from ubuntu.com and burnt it to DVD. Actually I tried with a bootable USB stick first, but the laptop refused to acknowledge its existence. So I tried the DVD. Here's what happened:
First attempt: I put the DVD in, switched on and hoped for the best. Purple screen with keyboard and stickman appeared, but I didn't do anything. Eventually this changed to the word 'ubuntu' with flashing dots. After a loooong time this changed to a grey screen. After another loooong time I got a purple screen with a few symbols on the bar along the top, but my cursor had disappeared. That's how it stayed forever, so I judged the attempt as failed.
I trawled the forum for possible solutions, then:
Second attempt: After the purple keyboard-stickman screen I got into the boot options (F6) and selected NOMODESET, and 'Try Ubuntu without installing'. Result: 'ubuntu' and flashing dots, then black screen.
Third attempt: same as second, except this time I selected ACPI-OFF and again 'Try Ubuntu without installing'. Result: same as second attempt.
Apologies for the verbosity, but I'm hoping someone can tell me where I'm going wrong.
I did a CHECKSUM on the iso image, and the DVD is ok as well.
I know you are going to ask me about technical specs, not sure about the answer:
CPU 2.80 GHz
37.2 GB
192 MB of RAM
ATI Mobility Radeon 7000IGP (this is the only graphics information I could find)
Any advice?

---

### Post by sudodus on 2015-09-22
Welcome to the Ubuntu Forums :-)

You need 2 GB RAM or more to run a current version of standard Ubuntu. The CPU is probably good enough for ***Lubuntu*** (or maybe ***Xubuntu*** and ***Ubuntu MATE***), but I would say that you need at least 512 MB RAM to Lubuntu to work reasonably well and 1 GB for the other two flavours of Ubuntu.

See these links

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

[Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

I suggest that you either try to find more RAM (maybe second hand from some other old computer) or try an ultra-light linux distro, for example ***Wary Puppy***, ***TahrPup*** or ***Tiny Core***.

Another option is to try ***ToriOS***, which is not released yet, but worth testing.

---

### Post by Wraenna on 2015-09-22
Thank you! That makes sense, that's why the poor thing was whirring away and not getting anywhere. I'll see what I can do, thanks for the advice.

---

### Post by grahammechanical on 2015-09-22
Are you sure it is only 192 MB RAM? This link says 512 MB RAM. Which still excludes Ubuntu. The link gives next to no information about the power of the video adapter and that is as important as the power of the CPU and the amount of RAM.

Some video adapters on these XP type machines cannot run Unity 3D which is what Ubuntu uses for a user interface. To run Ubuntu with Unity 3D we need a video adapter that can do hardware accelerated 3D rendering and from 512 MB to 1GB of its own memory. Otherwise all the work of video rendering has to be done by the CPU in software. And if the video adapter uses some of the RAM for its memory there is even less RAM for the OS.

OOPs

[http://www.toshiba.co.uk/discontinued-products/satellite-a60-106/](http://www.toshiba.co.uk/discontinued-products/satellite-a60-106/)

Regards.

---

### Post by Wraenna on 2015-09-22
Sorry, that was me not giving the exact information, the laptop is from the Satellite Pro Series, which has only half the hard disk size and half the RAM. It's still supposed to have 256 MB, but when I looked it up in Properties on the actual machine it told me 192 MB. I couldn't find anything about the video adapter, all it said was 'Legacy video controller' or some such. Anyway, as you point out, Ubuntu is not going to work either way on this machine - I'll go away and ponder what I will do.

---

### Post by sudodus on 2015-09-22
Try one of the ultra-light linux distros :-)

Play with it. Maybe you can use it for email and (text) chats, and to write documents. But do not expect it to work very well to browse the internet, and other tasks, that need a lot of graphics capability nowadays.

---

### Post by Wraenna on 2015-09-23
That's good advice, thanks. I have another laptop which I use as my main computer, I was planning to use this old one just to get to know Linux a bit and maybe write documents, but generally just to play around and learn something new.

---

### Post by sudodus on 2015-09-23
Good luck :-)

---

