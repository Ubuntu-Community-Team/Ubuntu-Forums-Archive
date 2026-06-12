---
title: "Problem rebooting computer an reinstalling Ubuntu"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by nadav3 on 2014-10-08
Hallo everybody,

I have been working with an old version of Ubuntu (10.04). Recently,  things had stopped functioning properly and I have decided to finally upgrade. This is where the real problem started. I am sure that in a very layman-fashion I have made some sort of a mistake ‘cause upgrading from the Update Manager is now impossible. And while trying to get Skype to work again I have somehow managed to make Firefox malfunctional... 

Long story short, I just wanna reboot my computer and install a newer version of Ubuntu on it. I tried, following the instructions on help.ubuntu.community, doing it with a cd. But every time a tried restarting my computer with the cd in it nothing came up. Than I thought, perhaps something went wrong in the process of burning the cd, so i did that (several times) again. Didn't work.

So, anybody care to give some advice / crash-course to the 21th Century...

Thanks in advance,
Nadav

---

### Post by nadav3 on 2014-10-08
Hallo everybody,

I have been working with an old version of Ubuntu (10.04). Recently,   things had stopped functioning properly and I have decided to finally  upgrade. This is where the real problem started. I am sure that in a  very layman-fashion I have made some sort of a mistake ‘cause upgrading  from the Update Manager is now impossible. And while trying to get Skype  to work again I have somehow managed to make Firefox malfunctional... 

Long story short, I just wanna reboot my computer and install a newer  version of Ubuntu on it. I tried, following the instructions on  help.ubuntu.community, doing it with a cd. But every time a tried  restarting my computer with the cd in it nothing came up. Than I  thought, perhaps something went wrong in the process of burning the cd,  so i did that (several times) again. Didn't work.

So, anybody care to give some advice / crash-course to the 21th Century...

Thanks in advance,
Nadav

---

### Post by yancek on 2014-10-08
> upgrading from the Update Manager is now impossible

Support for the Desktop version of Ubuntu 10.04 ended over a year ago which is why your attempt to upgrade failed.

Did you download the Ubuntu iso file from the Ubuntu site?  If you did, you will notice that the file is over 900MB and won't fit on a CD.  Are you actually using a DVD?  Did you burn the iso with the "burn as an image" option, at a slow speed?  Did you change the boot priority in the BIOS to boot the DVD before the hard drive?

---

### Post by nadav3 on 2014-10-08
I downloaded it from the Ubuntu website and used a DVD. 
I didn't burn the iso with the "burn as an image" option, at a slow speed. Could you please explain to me how do I that? And how do I change the boot priority in the BIOS to boot the DVD before the hard drive?

Greetings,
Nadav

---

### Post by zvacet on 2014-10-08
Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM[/URL")? If you did and everything is O.K. burn iso on lower possible speed. In BIOS select CD as your first boot device, and after that there is no reason not to boot in new Ubuntu.

---

### Post by nadav3 on 2014-10-08
thank you. could you please tell me how to set up my bios then?

---

### Post by ian-weisser on 2014-10-08
> **nadav3 said:**
> And how do I change the boot priority in the BIOS to boot the DVD before the hard drive?

Every manufacturer does it differently.
You watch your screen really carefully during POST and look for the 'boot options' or something similar. Usually while the manfacturer's logo is splashed on the screen.

---

### Post by mörgæs on 2014-10-08
Please stop multiposting.
Threads merged.

---

### Post by yancek on 2014-10-08
Not knowing which operating system or CD/DVD burning software you are using it will be difficult to explain this.  With the burning software, you will need to check the various options on burning but there should be a choice to "burn as an image" or something similar and of course, use the slowest speed option available.  Entering the BIOS is done by tapping a specific key on boot and this is usually shown at the bottom of the screen when you initially boot, usually says "use ?? key to enter setup.  The ?? would be replaced by whichever key is needed, often the F2, F10, Del or some other key.  It depends on the manufacturer and you will just have to watch the screen when you boot.

---

