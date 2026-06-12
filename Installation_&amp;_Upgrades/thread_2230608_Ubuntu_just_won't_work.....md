---
title: "Ubuntu just won't work...."
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by nnvt on 2014-06-20
Hello everyone,


I've been trying to install the latest version of ubuntu (well it doesn't really matter since it happens on every distro) After installation is complete my system reboots and says that it's in low graphics mode! Well ok lets install the display drivers then so after installing these drivers (again if i install fglrx fglrx-amdcccle from terminal or from a .run file it doesn't make a diference) the os boots and unity doesn't work and it pops up with a error saying xorg is not working. That's were I usually give up and shutdown my computer but that's not the weirdest thing! The computer boots up fine the same day ubuntu was installed but the next day: this happens: [https://www.youtube.com/watch?v=7bsadefYnek&feature=youtu.be](https://www.youtube.com/watch?v=7bsadefYnek&feature=youtu.be) 

the ubuntu logo pops up and then it reboots with no errors or log :/ and a full reinstall is required for it to work again for 1 day!


can anyone please help me fix this because i'm really getting tired of it and it has been bothering me for over 2 months

My pc specs are: AMD A10-4600m 

8 gigs of ram

amd radeon 8670M together with the 7660G integrated in the apu


thanks,

nnvt

---

### Post by rahul4557 on 2014-06-20
After installing try the following

goto terminal and type
> sudo apt-get update

then goto "Additional Drivers" from search in unity dash
Select the binary driver that is (proprietary,tested)
click "Apply Updates"

---

### Post by xc3RnbFO8P on 2014-06-20
When you start Ubuntu from Boot Manager click on advance option in Grub window and run recovery mode
choose Network and then repair broken package 
Otherwise Network > Root prompt and try to change display driver

---

