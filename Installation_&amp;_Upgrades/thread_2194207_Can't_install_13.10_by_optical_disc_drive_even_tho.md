---
title: "Can't install 13.10 by optical disc drive even though disc drive is fine"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by kavyasaraswat on 2013-12-17
Hello folks, 

    I am a newbie Ubuntu user. I want to upgrade my version to Ubuntu 13.10 by making a fresh install. I downloaded the ISO image of 64 bit version of Ubuntu 13.10 and burned it on a DVD. I also checked the image by doing checksum. The optical disc drive is working fine as it mounts other CD and DVDs. But when I try to install Ubuntu 13.10 by using live DVD then I can only see the contents of DVD after my version(13.04) of Ubuntu loads. The menu to try Ubuntu or install Ubuntu does not show up when I restart my HP desktop. It just logs in to my account and loads Ubuntu 13.04. To say it simply, I can't do a fresh install of Ubuntu 13.10 because the menu to install it does not show up during start up. 

Would you kindly enlighten me to install 13.10 by a live DVD. I've burned three DVDs of 13.10 and checked all of them but still I can't use those DVDs to install 13.10.


Thank you very much in advance.

---

### Post by mörgæs on 2013-12-17
Hi, welcome to the fora.

Did you set BIOS to boot from CD/DVD?
Have you tried installing from USB?

---

### Post by kavyasaraswat on 2013-12-17
[FONT=comic sans ms][/FONT]Thank you very much for the reply :)

I upgraded from 12.10 to 13.04 by using a live DVD so I think BIOS are already set [FONT=comic sans ms][/FONT]to boot from CD or DVD. I haven't tried to install 12.10 by using a live USB.

Would you agree the with following solution :

1. I press DELETE as soon as the system starts up and so I can enter into BIOS,
2. Now I choose boot options from the start-up menu and choose boot from CD,
3. Then I click on 'install Ubuntu' from the menu to install 13.10 and erase 13.04 in the process.

Is the aforementioned process just a workaround?
Can I follow it to install 13.10? Remember that the live DVD still does not shows up by itself and I have to entrer BIOS to boot from DVD.

If there is any other process to set BIOS to boot from DVD then kindly tell me.

My desktop is HP 110-025il with 4GB DDR3RAM and core i3 3240T CPU. I don't use Windows at all and have installed only Ubuntu on it :KS

Thanks again in advance :)

---

### Post by Bucky Ball on 2013-12-17
The above is fine. Just get into BIOS, boot from DVD, SAVE the changes and exit, machine boots from dvd, install Ubuntu. Done. I see no problem.

---

### Post by fantab on 2013-12-17
It is a good practice to first 'Try Ubuntu (without installing)', before you actually install Ubuntu.
After 'Try Ubuntu', check if all the features/hardware on your PC is working and importantly establish connection to internet.
Then install Ubuntu from 'desktop' option to install Ubuntu.

---

### Post by mörgæs on 2013-12-18
Still, if for some unknown reason the DVD approach fails I recommend creating an installation USB stick with Unetbootin and install from that.

---

### Post by Bucky Ball on 2013-12-18
And also ... 

Video and wireless not working on a 'Try Ubuntu' session does not mean they will not work on a hard drive install. Some hardware needs to install third-party drivers that can only be installed to a hard drive install.

So, by all means, 'Try Ubuntu' before installing, but that by no means necessarily gives you the full story as to how a hard drive install will go, but generally close to it. ;)

---

