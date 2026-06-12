---
title: "Windows 10 and Ubuntu 15.01"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by john-c-at95 on 2015-06-01
I have Windows 7 and Ubuntu 15.01 would like to try Windows 10 along side my Ubuntu 15.01 what would be the difficulties if any?

---

### Post by ubfan1 on 2015-06-01
Assume the worst and have everything backed up.  You might try a virtual machine first if you have the spare disk space.  VMware offers a convert program to create a VM from a running Windows OS (my XP on an 80G disk produced a 50G file for the VM), then update the VM.  The more conservative among us eagerly await your report of success!

---

### Post by oldfred on 2015-06-01
UEFI or BIOS?

If BIOS best to have all Windows installs in primary partitions, so each can be booted from grub menu. Otherwise you can only boot from Windows BCD options. And you have to make sure the fast startup or always on hibernation is off, just like in Windows 8.

---

### Post by RobGoss on 2015-06-01
Hello and welcome to the forum, As far as I know you can try Windows 10 Technical Preview but you would have to be signed up with Windows insider program. I think Windows 7 and 8, user have been invited to join that program including my self. One thing you should know you cannot revert back to your old Windows 7 OS if things don't work out unless, you have your Windows 7 disk that you got with your computer.

Windows 10 will be released July-29-2015 as far as I know to the public....

---

### Post by Mark Phelps on 2015-06-02
Assuming you want to keep your Win7 intact (in case you don't want to move to Win10 permanently), then I would recommend that you download and install Macrirum Reflect (in Win7), make an image backup of your Win7 setup to an external drive, and use the option to create a Boot CD/USB -- which would be needed later to restore Win7 from the backup.

When you do an in-place upgrade of Win7/8/8.1 to Win10, it replaces what you have, and as RobGoss mentioned, you can't then go back to Win7 should you decide you want it back.

---

### Post by john-c-at95 on 2015-06-02
A bit nervous, I might just wait and see how others get on first. Thanks for all the support.

---

### Post by RobGoss on 2015-06-02
Thanks **Mark,** also as Mark stated, you can clone your Windows  OS in case anything goes wrong. I my self use[ **Clonezilla **]("http://clonezilla.org/downloads.php")and it seems to work flawlessly. I never took the plunge in to Windows 10- because I don't really see much coming in this version besides the new start menu and maybe a few other things that their bringing back.

 I mean don't get me wrong I've been using Windows for about 17- years and for the most part I have learned a lot from using it including never buying virus protection because I had gotten so may virus when I started I learned to keep my machine virus **FREE**.

Ubuntu has opened my eyes to a whole new world of distributions and trouble free and running 5 - plus machines on a daily bases I know have only one machine running Windows, everything else is running Linux...

What ever choice you make I wish you the best I say Ubuntu for ever :)

---

### Post by Frogs Hair on 2015-06-02
You should get a notification from Microsoft to reserve a free upgrade To windows 10 from 7 or 8 when it's released later this year(July?). The notification appeared in the task bar of my computers yesterday. In the past MS has not upgraded development versions to the final release so you would end up re-installing Windows 10 when released.

---

### Post by RobGoss on 2015-06-02
> **john-c-at95 said:**
> A bit nervous, I might just wait and see how others get on first. Thanks for all the support.


Remember you can always fixes what's broken.

---

### Post by Mark Phelps on 2015-06-03
> **Frogs Hair said:**
> In the past MS has not upgraded development versions to the final release so you would end up re-installing Windows 10 when released.

True ... but in this case, MS is handling it differently.  What used to be called RTM (Release To Manufacturing), is now being called GA (General Availability), and not only will the pre-release Windows Insider versions get updated, but the Inside program will continue past GA, allowing those in the program to continue to get early versions of updates.

---

### Post by Frogs Hair on 2015-06-03
Mark, that would make sense because 10 is the last planned release and it will simply upgrade and update as needed from that platform. I'm waiting until 7-29 since the conformation has already been sent. Cortana will only be included in certain locations if the free upgrade path is used according to one article I've read.

>  [COLOR=#444444][FONT=Helvetica]Cortana will only be available in the US, Canada, UK, China, France, Italy, Germany, and Spain at [/FONT][/COLOR] [http://www.theverge.com/2015/6/1/8696949/windows-10-feature-loss](http://www.theverge.com/2015/6/1/8696949/windows-10-feature-loss)

---

### Post by dFlyer on 2015-06-03
Beware. I remember reading somewhere that with Win 10 you will not be able to dual boot with linux. Don't remember where I read it but you may want to do a web search before you try it.

---

### Post by Mark Phelps on 2015-06-04
> I remember reading somewhere that with Win 10 you will not be able to dual boot with linux.

Then, I would not trust the source of that comment ... as I am dual-booting with Win10 and Linux just fine.

---

### Post by oldfred on 2015-06-04
I believe the comments were that Microsoft was not going to require that manufacturers allow users to turn off Secure Boot.

But Ubuntu uses the same key as Microsoft and can install in secure boot mode.

We may just have to wait to see what vendors do as they do not seem to totally follow UEFI standard, anyway. 

This is more for what systems may qualify for updates:
[http://www.microsoft.com/en-us/windows/windows-10-specifications](http://www.microsoft.com/en-us/windows/windows-10-specifications)

---

