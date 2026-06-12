---
title: "Ubuntu Install: Unusual Situation"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by akshaypande1989 on 2011-09-11
Hi everyone!

I bought an Asus EEE PC 1201T yesterday which has AMD 64 Dual Core MV40 architecture and came compulsorily with Win 7 starter. I wanted to dual boot with Ubuntu 10.4.3. These are the events of yesterday:

1) The computer had a large D: in which I installed Ubuntu 10.4.3 LTS **i386** (by mistake, out of habit, because I had intel architecture in my earlier laptop) outside of Win 7. It went fine and I was satisfied. The GRUB boot loader started showing up on startup as expected.

2) My Win 7 got corrupted or something after I used the internet and I wanted to use the in-built Win Vista recovery partition to save it. This recovery option also showed up as a boot option in GRUB. So I started the recovery and it erased my C: which had Win 7. Then something very unusual happened:

On automatic restart, I couldn't see the "American Megatrends Inc" page and came directly to the GRUB booter. The recovery process could simply not be completed.

3) I thought, "no problem, I can live without windows" and was fine. Then I found out about the AMD64 version of Ubuntu 10.4 and I had a real wish to install it as it fits my architecture better. So I prepared the install disc.

4) But now because on booting I come directly to GRUB, I cannot access my BIOS page. I don't have an opportunity to press DEL to invoke BIOS and so I can't do a fresh install. 

Can I somehow solve the issue with an alternate install? If yes, what are the steps? 

Please help!

Warmly
Akshay Pande

---

### Post by pytheas22 on 2011-09-11
As long as you can get into the grub menu, you should be able to custom-edit one of the boot entries and make it boot to a live USB that way.  You could also probably make it boot to a live CD, but that would be more complicated; I would recommend simply making a live USB.  There are directions for that at [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).

I think the button you have to press to edit your grub entry is the letter 'e', but I'm not positive.  Once you're into the screen where you can edit the boot entry, erase everything (use control-k to delete a line) and put in the lines you need to boot your live USB.  The exact parameters depend on your situation but you should be able to figure them out by reading [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  Once you've entered everything, press control-x to boot.  Note that none of these changes to your grub entry are permanent; they will be forgotten when you reboot the computer.

By the way, this may not be worth the trouble because the amd64 build of Ubuntu doesn't actually fit your architecture better.  i386 and amd64 builds work equally well on both Intel and AMD CPUs.  The difference between them is that i386 supports only 32-bit processors (both Intel and AMD), while amd64 is for 64-bit chips (again, both Intel and AMD).  If you have more than 4 gigabytes of RAM in your computer, using an amd64 build of Ubuntu will allow you to use more memory because i386 kernels can only address up to 4 gigabytes; otherwise, there's no major difference between i386 and amd64 and you can use either one regardless of whether your processor was built by Intel or AMD.

---

### Post by akshaypande1989 on 2011-09-11
It isn't working out. I copied the default menu entry from /boot/grub/grub.cfg

```
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 608f2b61-a6e5-4335-8ce5-ff089a2ed56a
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=608f2b61-a6e5-4335-8ce5-ff089a2ed56a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
```

pasted it in /etc/grub.d/40_custom after the headers and changed it to

```
menuentry 'Live CD Ubuntu AMD64' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 608f2b61-a6e5-4335-8ce5-ff089a2ed56a
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=608f2b61-a6e5-4335-8ce5-ff089a2ed56a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
```

I restarted ensuring that only my pen drive was connected to the laptop but the entry doesn't show up in the menu.

I also tried what you advised, modifying the menu entry on startup with the 'e' key, but it still boots from my hard drive.

What am I doing wrong?

---

### Post by Quackers on 2011-09-11
Power the pc off completely and unplug any peripherals then leave it for a minute. Then after pressing the power button to start it keep tapping the Del key (if that's the correct key to access your pc's bios - check that). There is no way that grub will supercede the bios key that I know of.

---

### Post by akshaypande1989 on 2011-09-11
Dear Quackers,

It worked!

I rebooted and pressed the fleet of buttons on the top row of my keyboard like a madman. The button turned out to be F2 and the ASUS page showed up :KS!! Then came the reassuring blue BIOS setup screen and it was smooth from then on.

I also set a BIOS Setup password because I realised that it would be too easy for anyone to erase my computer and install any OS.

I am also thankful for the GRUB advice because I got to learn a bit about GRUB2 in the process :)

Thanks so much, and very warm wishes!

Akshay Pande

---

### Post by Quackers on 2011-09-11
I'm glad that things got sorted out :-)
Happy Ubuntuing!

---

