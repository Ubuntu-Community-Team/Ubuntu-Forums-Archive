---
title: "Ubuntu stuck at boot and doesn't load from LIVE USB either"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by pietro-dellabriottaparolo on 2017-10-30
Hi all,


ATM i'm sitting here with a virtually dead laptop that won't respond to any input. Let's recap what the situation is:

- I have a MacBook pro on which I install ubuntu (16.04) as the only OS 
- Everything was working fine until today when, while I had my iphone plugged in i turned the laptop off and unplugged the phone right just when it was about to turn off completely. It gave me an error and the screen was unresponsive so i just turned the laptop off.
- Now when I turn it on i'm stuck at the [COLOR=#111111][FONT=Ubuntu]/dev/sda2: clean xxx/xxx files, xxx/xxx blocks 
[/FONT][/COLOR]- I tried entering recovery mode by clicking shift but nothing happened
- I used another machine to burn Ubuntu 17.10 into a usb drive 
- On boot the mac ignores the drive and just goes back to the same screen

I'd be really grateful if someone could help me with all this!

Thanks
[COLOR=#111111][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by sunbear-c22 on 2017-10-31
I am not an expert. I notice you wrote [FONT=Courier New]/dev/sda2: clean xxx/xxx files, xxx/xxx blocks[/FONT]. I am thinking that if  your disk needs cleaning, you can use a ubuntu boot/install disk and boot your system from there. E.g., if you have a 17.10 install USB, boot from this usb and click try 17.10. After entering Ubuntu, you can open a terminal type ```
e2fsck -p /dev/sda2
``` to automatically fix them. Have a read of the below writeup to see if they are relevant to you.

[https://www.systutorials.com/docs/linux/man/8-fsck.ext4/](https://www.systutorials.com/docs/linux/man/8-fsck.ext4/)
See number 10. in [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

---

