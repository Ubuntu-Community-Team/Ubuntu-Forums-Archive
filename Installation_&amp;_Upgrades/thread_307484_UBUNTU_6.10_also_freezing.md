---
title: "UBUNTU 6.10 also freezing"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by abby on 2006-11-26
I just downloaded the 6.10 DVD iso and when i reboot my PC it uncompresses the kernel and then a screen with KUBUNTU logo comes with a progress bar sort of thing which doesnt update. It sits there doing nothing. I have a brand new athlon 64 3700+ system with 1 gig RAM 15" , nvidia geforce 6150 LE and an integrated DVD burner with 250 gigs of hard disk. Whats wrong??

---

### Post by abby on 2006-11-26
I just downloaded the UBUNTU 6.10 CD iso , thinking something was wrong with kubuntu but again when i reboot my PC it uncompresses the kernel and then a screen with UBUNTU logo comes with a progress bar sort of thing which does not change for ever. It sits there doing nothing. I have a brand new athlon 64 3700+ system with 1 gig RAM 15" , nvidia geforce 6150 LE and an integrated DVD burner with 250 gigs of hard disk. Whats wrong?? I tried the safe mode as well from the CD and it does the same thing.

---

### Post by taurus on 2006-11-26
How fast did you burn the ISO image anyway?  Sometimes burning too fast can could problems.  So, see if you can burn it at a slower speed like 4x!

---

### Post by PurplePenguin on 2006-11-26
Put the disc in, reboot and instead of choosing "Start/Install", go down to "Check disc for errors".  Let that run and see if it comes up with anything.

---

### Post by abby on 2006-11-26
Even check disc gets stuck at that screen.

---

### Post by taurus on 2006-11-26
It only means there is something wrong with that disc.  Again, did you run the md5sum to check the integrity of the ISO image before you burn it and how fast did you burn it!  Look at this link especially the section on how to check the integrity of the ISO image...

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by abby on 2006-11-26
Verfied MD5  also burnt 2 discs at lowest speed of my burner. It still gets stuck at that screen.Ubuntu logo and a progress bar with 10 vertical stripes 5 cms apart CD whirrs for a bit before it stops and there is absolute mum for always untill i eject CD and it still is sitting at that screen. i have to restart to boot back to windows. I am getting a bit frustrated after wasting so much bandwidth and time downloding DVD then CD and no use. Maybe i will give open suse a chance if i dont figure out with the help of u guys whats going on.

---

### Post by taurus on 2006-11-26
If you have the DVD version, try using the alternate CD which I believe is also available from the DVD!!!

---

### Post by abby on 2006-11-26
Whats the difference in alternate CD?

---

### Post by taurus on 2006-11-26
The alternate CD allows you to install Ubuntu with text mode in case the LiveCD is having a problem with your graphic card.  Besides, you don't have to boot it up first before you can install it.  You install it from the CD right away...

---

### Post by abby on 2006-11-27
Ok i tried with alternate CD as well. I started it to install in text mode and it froze again after showing booting the kernel. A cursor just sits there blinking doing nothing. I waited about 5 minutes and then took out the cd again. Idon't know whats wrong. This is annoying now. already wasted 3 DVD's and 5 CD's.

---

### Post by Jonathan987 on 2006-11-27
this sounds like my first experience with ubuntu....it turned out to be a memory error thing. so...I recommend that you check your memory.....it's one of the options on the alternate cd...

let us know what that comes up with...


good luck!

Jonathan

---

### Post by abby on 2006-11-27
Nope i have checked my memory its fine. I have a feeling it is looking for some device which is not there. I don't have a floppy installed and maybe its looking for that. Can it cause the problems as mentioned? Also, how to disable looking for floppy.

---

### Post by jimrz on 2006-11-27
> **abby said:**
> Nope i have checked my memory its fine. I have a feeling it is looking for some device which is not there. I don't have a floppy installed and maybe its looking for that. Can it cause the problems as mentioned? Also, how to disable looking for floppy.

do you have any usb devices attached? if so, try unplugging them before you start the install

---

### Post by phoenixdreaming on 2006-11-27
I'm having problems with Ubuntu and Kubuntu install CDs freezing too. Yet they worked earlier today, and I haven't changed anything about my computer set-up. I'll try unplugging USB devices as you suggest, jimrz; won't do any harm if it doesn't work anyway.

---

### Post by countolaf on 2006-11-28
Abby, I am having the same problems as you are, and have verified the MD5 sum of the ISO before burning; I even tried downloading and burning the image again from another mirror. I have an Athlon 64 3500+ SKT 939 which I have tried on two different boards, from two different manufacturers, but both have the ATI RS480 / Radeon Xpress 200 Chipset -- does your motherboard have this chipset? I have tried with onboard video and also with an ATI Radeon X300 PCI Express video card. I'm starting to suspect the chipset...

PS I have also verified the system memory on both boards, both boards have OK memory per the utility included on the Ubuntu CD.

---

### Post by unisol on 2006-11-28
are you using the 64 bit version? do you have raid on your system

---

### Post by abby on 2006-11-28
yes i am using 64 bit version. i don't have RAID devices. I tried putting in acpi=off and this time it went a little further but again froze. I am surprised that UBUNTU which is touted as a great windows replacement can be such a pain to install for a technical person. I wonder why we keep talking about linux as a replacement when it can't even install. Imagine a layman trying to use any linux distro. There are so many flaws. Won't detect SATA hard drives boot a seperate kernel, advanced power config needs to be turned off....blah blah.............What is God's name will a layman know about this. Cmmon proponents of Linux and open source it's time to bow down to Windows or Mac. It has been almost 15 years since linux began evolving and it still is no where near usable and installable forget being a replacement to mighty windows. This just confirms that a corporate backing is needed for any product to work. Its not like Unix core cannot have a good GUI look at MAC. It beats windows to core and is super good, but linux is only for educational and technical community it's not a replacement.

---

### Post by Lord Illidan on 2006-11-28
> **abby said:**
> yes i am using 64 bit version. i don't have RAID devices. I tried putting in acpi=off and this time it went a little further but again froze. I am surprised that UBUNTU which is touted as a great windows replacement can be such a pain to install for a technical person. I wonder why we keep talking about linux as a replacement when it can't even install. Imagine a layman trying to use any linux distro. There are so many flaws. Won't detect SATA hard drives boot a seperate kernel, advanced power config needs to be turned off....blah blah.............What is God's name will a layman know about this. Cmmon proponents of Linux and open source it's time to bow down to Windows or Mac. It has been almost 15 years since linux began evolving and it still is no where near usable and installable forget being a replacement to mighty windows. This just confirms that a corporate backing is needed for any product to work. Its not like Unix core cannot have a good GUI look at MAC. It beats windows to core and is super good, but linux is only for educational and technical community it's not a replacement.

Do you honestly think everyone has the same problems as you did?

---

### Post by abby on 2006-11-28
> **Lord Illidan said:**
> Do you honestly think everyone has the same problems as you did?

looking at the forums, if not everyone a significant number of people did.

---

### Post by Lord Illidan on 2006-11-28
> **abby said:**
> looking at the forums, if not everyone a significant number of people did.

Granted. This is a SUPPORT forum. We wish that all the guys who had success with Ubuntu come here to say hello, but usually no, we get the guys who come in and say "LINUX SUCKS!! IT DOESN'T WORK FOR ME!! IT DOESN'T WORK ON THE DESKTOP. I'M GOING BACK TO WINDOWS!!".

Let me give you some pointers:

1. Give it time. I spent a couple of years getting used to Linux.
2. Use DVD/CD -RWs.. Save money.
3. Be more civil. More people will help you.
4. Where did it freeze last time?

---

### Post by abby on 2006-11-28
I am not complaining. I have two machines which have Ubuntu running, but it has never been without problems that i managed to install it. this time its more painful. It gets stuck on the screen where the progress bar just keeps bouncing back and forth right after booting. I am going to try the text mode tonight to get into the specifics. All i am complaining about is that it should be a peace of cake for anyone.

---

### Post by raul_ on 2006-11-28
I don't mean to be rude here...but windows/mac users (i guess u're one) keep saying that Linux won't ever be ready for the "common" (???) user to use. Let  me give u the breaking news of the day: Linux developers don't give a damn :P Linux is not supposed to sell more, it's not supposed to generate more profit, it's all about building a better OS everyday. If u say "oh i'll just give up and go back to my OS X" and slam the door, no Linux developers will care. If i was you, i'd ask for a refund anywayz...

Being "nicer" now, i still think it's a CD error but i'm just curious: did u try the CD on a different computer? like your neighbour's computer or something like that...if it doesn't work, it's definitly a burning error, it it works, at least u know it's some sort of compatibility problem (although i have to say that i don't believe that after all those cd's/dvd's burned, not a single one worked...)

By the way, are u installing the 64 bit or 32 bit version? if u're using the 64 bit i would recommed using the 32 bit,from what i've read...

---

### Post by abby on 2006-11-29
i am using 64 bit version. also, the dvd seems to be fine. it just displays randomness. I tried appending noapic and acpi=off and it started the live cd. I hit install this time and it goes till partitioning and then freezes. I hit restart and this time with same options it gets stuck with a console prompt and no live boot. i don't know whats wrong the image or the 64 bit version or something else. could it be because of the lightscribe drive in my system??

---

### Post by mssever on 2006-11-29
I've gathered from other threads that the 64-bit version is a bit buggy. The 32-bit version works fine on 64-bit computers--they just behave like 32-bit computers. You might want to try the 32-bit version and see what happens.

I suspect that the reason that 64-bit doesn't work so well is because it's newer and has a smaller user base. One way to help to improve the 64-bit version would be to try to use it and file bug reports...

---

### Post by unisol on 2006-11-29
i agree with msserver file bug reports and try the 32-bit version

---

