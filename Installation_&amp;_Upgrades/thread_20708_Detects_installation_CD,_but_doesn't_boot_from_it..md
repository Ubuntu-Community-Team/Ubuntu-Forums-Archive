---
title: "Detects installation CD, but doesn't boot from it."
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by Asycas on 2005-03-18
I'm installing from a the Hoary Preview installation CD that I got of BitTorrent. While booting, the CD is detected fine, and the Ubuntu screen comes up and asks me to press enter to accept default installation settings. When I do that, it loads some stuff, and then says 'Ready.' However, after that, the computer just reboots without loading the installer and begins the whole frustrating cycle again...   :? 

Any ideas?

---

### Post by bored2k on 2005-03-18
[QUOTE=Asycas]I'm installing from a the Hoary Preview installation CD that I got of BitTorrent. While booting, the CD is detected fine, and the Ubuntu screen comes up and asks me to press enter to accept default installation settings. When I do that, it loads some stuff, and then says 'Ready.' However, after that, the computer just reboots without loading the installer and begins the whole frustrating cycle again...   :? 

Any ideas?[/QUOTE]
 Before pressing enter in the Ubuntu ugly screenie, press F2 for boot parameters, see if you can find any that Matches your computer specifications or that just sticks out for you.

---

### Post by Asycas on 2005-03-18
No... it didn't work... I tried the more general options as nothing specifically applied to me, but it's still rebooting merrily...  :?

---

### Post by Asycas on 2005-03-18
I've tried installing with the same CD on another computer, and it works beautifully... but it still can't boot with this computer =/

I've got a Compaq Presario SR1238AP from HP - any specific problems with my hardware?  :confused:

---

### Post by raju on 2006-07-15
**The issue appear to be in the BIOS. HP has locked down the system not to boot from linux !!! **Here is a quote from my chat with HP online support. The support person was helpful but I am a bit concerned here with the info I got. However let me wait for the email from HP before getting in to the next level of struggle .:-k 
[I]Rick: Welcome to HP Total Care for Desktops.
My name is Rick. How may I assist you today?
Rick: Hi Raj
Raj: Hi Good morning Rick
Raj: I have an issue with my SR1238AP desktop
Raj: the bios version is V6.0 / 3.15
Raj: When ever I try to boot with a linux CD the system just reboots
Raj: I searched net and find that this is a common issue with this model
Raj: Is there a latest BIOS that fix this issue?
Rick: Please give me five minutes while I check with the computer specifications and get back to you.
Raj: ok
Rick: Raj, Linux software is not compatible with HP computers.
Rick: Thank youy for staying online.
Rick: As of now there are no BIOS updates for your computer model.
Raj: I understand HP won't support linux
Raj: but why is it just not allowing to boot from a linux CD?
Rick: The Hardware on the Hp computer is not compatible with Linux at all. Hence it doesn't boot.
Raj: The issue here is If I want to change the OS prepackaged I can't do.
Raj: Thnaks Rick for the info
Raj: is there any way I can understand which component is not supported
Raj: I know intel pentium4 is supported and the generic DDR RAM is supported
Raj: the IDE/VGA components are also
Raj: supported
[B]Raj: so is it only the BIOS?
Rick: Yes the BIOS will not allow to boot through Linux.[/B]
Raj: OK. Will you please escalate it further to get a fix for the BIOS ?
Rick: Raj, I understand your concern. If BIOS update versions are updated, then it is available in Softwares and Drivers download page of Hp.com website.
Rick: [COLOR="Red"]***The updated bios in future too will not support Linux.***[/COLOR]
Raj: But Rick there is no new updates available now. As you said earlier
Raj: can you please log this as an issue and get som fixfrom the HP engineering team?
Rick: Sure, I will pass this chat to my Technical department and you will soon get an email regarding the details.
Raj: Thnaks a lot Rick. MUch appreciate your assistance. I will wait for the mail...
Rick: Sure. Is there any other technical issue that I can assist you with ?
Raj: No other issues Compaq PC Doctor certified my system perfect. :)
Raj: thank you
Rick: You are welcome. It has been a pleasure to assist you.[/I]

---

### Post by raju on 2006-07-15
[SIZE="4"]HP was very quick in reverting with some sensible solution. =D>  Here is the reply from the second level support...[/SIZE]
[SIZE="3"]So it is **not** HP's lock as mentioned before...[/SIZE]

[FONT="Verdana"][SIZE="2"]
Hi Raj,

Thank you for contacting HP Total Care.

This e-mail is a follow-up of your recent Chat session dated 07/15/06 you had with our online technician.

In order to boot to CD to install Linux OS onto your Hp computer, there 
are 3 ways:

**First method:** Format the harddisk completely and then install Linux CD. 
Dual boot is not possible if Win Xp Home edition is already present in 
the system.
[B]
Second method[/B]: Change boot sequence in the computer such that system 
boots only through CD drive which contains the Linux Cd. When you 
restart the computer press Esc key and change the boot sequence from the
menu there.

**Third method**: Create a bootable floppy of Win 98 from he following 
website:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

(directy ftp link is [http://www.troyedwards.com/downloads/BootDisks/boot98.exe](http://www.troyedwards.com/downloads/BootDisks/boot98.exe))

Use the bootable floppy that is generated from above link and restart 
the system using the bootable floppy. 

Then  change the  directories at the command prompt to \DOSUTILS and 
typed AUTOBOOT. This fired the CD up.

Then you can access the Linux Cd and install the software.[/SIZE][/FONT]

---

### Post by Forko on 2006-07-18
Is there any way to make it run from the live CD?

---

