---
title: "im sick with ubuntu"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by homunculus1179 on 2011-04-26
i dont know why other people say that ubuntu is this, ubuntu is that. but i not get the thing that people say. in 2weeks..i have format my laptop more then 10 times. if a search for the solution, nobody can give me right answer. it make me suck. they are many problem with ubuntu. if i format my laptop again. i think it will blow up. and now, i cant go back to window, because grub problem. oh god,help me..im tired.:confused::confused::confused::confused::confused::confused:

sorry for my bad english. im asian

---

### Post by Buntumatic on 2011-04-27
I do not see a support question here. 

These forums are about using and enjoying Ubuntu. I find your rant is off topic here.

---

### Post by homunculus1179 on 2011-04-27
sorry..firstly im using two os..window 7 and ubuntu..the problem is my nvidia graphic..in nvidia website, it say they have update driver for my nvidia gt 520m. but, i didn't work for me. when i restart, i just have blank screen. why this happen to me??

---

### Post by krapp on 2011-04-27
Do you have a Windows recovery disc?

---

### Post by homunculus1179 on 2011-04-27
> **krapp said:**
> Do you have a Windows recovery disc?

yes. but it didn't work too. grub problem. i dont know how to fix it

---

### Post by krapp on 2011-04-27
Read your computer's manual how to reformat your hard drive using your recovery disk.

If you boot from the disk (on my laptop I press ESC to choose where to boot from) you shouldn't see GRUB

[http://en.wikipedia.org/wiki/Boot_disk#Booting_from_a_disk](http://en.wikipedia.org/wiki/Boot_disk#Booting_from_a_disk)

---

### Post by Quackers on 2011-04-27
So did Ubuntu boot before you updated the Nvidia driver?

---

### Post by homunculus1179 on 2011-04-27
> **Quackers said:**
> So did Ubuntu boot before you updated the Nvidia driver?

no. just blank screen

---

### Post by Quackers on 2011-04-27
You need to do some reading before you take giant steps installing a new system. It's better to be prepared. Did the live cd boot to a desktop? Did you select "try ubuntu" before installing it?
Have you tried the nomodeset boot option?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by homunculus1179 on 2011-04-27
> **Quackers said:**
> You need to do some reading before you take giant steps installing a new system. It's better to be prepared. Did the live cd boot to a desktop? Did you select "try ubuntu" before installing it?
Have you tried the nomodeset boot option?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

yes,im using live cd and im try it..i dont know about nomodeset, and im not trying it..now im done fresh install, but the graphic still not working

---

### Post by beew on 2011-04-27
Well what is the model of your computer? Is it a laptop? If it is does it have  Optimus enabled?

---

### Post by homunculus1179 on 2011-04-27
> **beew said:**
> Well what is the model of your computer? Is it a laptop? If it is does it have  Optimus enabled?

this is laptop. my spec is acer aspire 4750g. intel i5 2410m, nvidia geforce gt 520m, 4GB ddr3 memory.

---

### Post by TBABill on 2011-04-27
Do you have Internet access during install? Normally the system will detect the nVidia and it will place an indicator in the top right portion of the screen to install proprietary drivers. If you are connected to the Internet the system will take care of installing, updating and installing the nVidia driver that is available in the repos (even if it's not the latest and greatest driver). Were you able to connect and do those things?

---

### Post by homunculus1179 on 2011-04-27
> **TBABill said:**
> Do you have Internet access during install? Normally the system will detect the nVidia and it will place an indicator in the top right portion of the screen to install proprietary drivers. If you are connected to the Internet the system will take care of installing, updating and installing the nVidia driver that is available in the repos (even if it's not the latest and greatest driver). Were you able to connect and do those things?

yes,im connect with internet..but im not sure about the updating driver

---

### Post by beew on 2011-04-27
> **homunculus1179 said:**
> this is laptop. my spec is acer aspire 4750g. intel i5 2410m, nvidia geforce gt 520m, 4GB ddr3 memory.

Your model does not work with Linux.

Check the specs
[URL="http://support.acer.com/acerpanam/notebook/2011/Acer/Aspire/Aspire4750G/Aspire4750Gsp2.shtml"]http://support.acer.com/acerpanam/notebook/2011/Acer/Aspire/Aspire4750G/Aspire4750Gsp2.shtml
[/URL]
Your laptop has Optimus enabled and it doesn't work in Linux. Even if the card is supported (with Nvidia proprietary driver) if used alone, it stops working when Optimus is enabled. Unless there is a BIOS switch to disable Optimus and choose the discrete card, there is no way for Linux to access the Nvidia card because under Optimus, the Nvidia card access display through the onbroad Intel card and becomes a hybrid with the latter.  You can only use the Intel card (and installing Nvidia driver would kill the system resulting in black screen) but the Nvidia card would still sit there and suck up power and generate heat, so the best you can hope for is to somehow switch off the Nvidia card and turn it into an expensive paperweight.

For more on Optimus 
[http://ubuntuforums.org/showthread.p...hlight=optimus]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus")
[URL="http://www.nvnews.net/vbulletin/showthread.php?t=153321"]http://www.nvnews.net/vbulletin/showthread.php?t=153321
[/URL]

You may also want to write to Nvidia. 

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

Not only does it not support Optimus in Linux, under Optimus, the Nvidia card would not work in Linux **at all** even though Nvidia supposedly "supports" the card with Linux driver.

Since most new Nvidia laptops are shipped with Optimus that means Nvidia  effectively stops supporting Linux on laptops,--unless the laptop manufacturers include a BIO switch to turn off Optimus,-- if that is the case they should be  at least upfront about it so Linux users will not waste money on these machines.

You can also write to the laptop manufacturer (acer) asking that a BIOS Switch for turning off Optimus be included.

Man you are totally off base in ranting against Ubuntu, it is not to blame for the Optimus disaster, write to the people responsible instead.

---

### Post by Buntumatic on 2011-04-27
Some progress has be made ... without manufacturers help ... [http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html](http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html)

To OP - this your chance to contribute.

---

### Post by beew on 2011-04-27
> **Buntumatic said:**
> Some progress has be made ... without manufacturers help ... [http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html](http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html)

To OP - this your chance to contribute.

There is progress for sure and the undertaking is interesting and important from a developmental point of view, but unless I am mistaken by "working" they mean being able to use the Nvidia card with nouveau driver. While I have a lot of respect for the nouveau developers and think that they do valuable work, this is hardly "working" if that means getting the full functions out of the card. With nouveau there is no hardware acceleration (VDPAU), no cuda, and no up to date version of OpenGL, there is really no point in spending the money on a high performance Nvidia card at all if you have to use it with nouveau (at least at present)

But I would also ask the OP to contribute since he has gotten the laptop already.

---

### Post by Ken UK on 2011-04-27
If the LiveCD didn't work out of the box you should have expected some work on your hands from the start. I've been in the same boat and still am to some degree.

Can't you access your windows through GRUB or does that not load either? If you want to get rid of GRUB to get access to windows again just use the windows recovery disk to re-write the master boot record to remove GRUB.

---

### Post by homunculus1179 on 2011-04-27
thank you to all that helping me. my acer back to window. but my hp work well on ubuntu.

---

### Post by samriggs on 2011-04-28
> **Buntumatic said:**
> I do not see a support question here. 

These forums are about using and enjoying Ubuntu. I find your rant is off topic here.

**Please tell me your joking with this statement**
The poor guy is begging for help you say this crap! Especially when it's under installation and upgrades which is what the guy is talking about and asking help for.
Please don't help anyone else your useless and saying this forum is for enjoying and using ubuntu I guess its not for getting help or asking questions then.
Gawd I can't believe your actually saying this crap.
Sorry folks but when I seen this it made me sick.
There is tons of good help here don't let this person stop you from seeking help.

---

