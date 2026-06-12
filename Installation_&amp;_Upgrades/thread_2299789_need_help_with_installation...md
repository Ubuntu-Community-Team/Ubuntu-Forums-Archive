---
title: "need help with installation.."
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by joe9450 on 2015-10-21
i am trying to install ubuntu but have been away for awhile and forgot the procedure..i used to just wipe a hd clean with killdisk and install from a dvd.l.ok, here's what's been happening:i downloaded ubuntu(15.04 i believe) and extracted it onto the hd,in its folder) and onto a ,,supposedly bootable, sd card (i've had no luck with the sd card route). i have an asus n550jx and i think its this uefi type bios..like i said,its been awhile and i've been at the sd card install attempt for days now (trying different combinations in the bios settings).now, i give up on the sd card and for get how to even install it onto the hd..like i said,its extracted into its own folder.i try running the executable and get a "wubi not (something) with efi" type message..i wish i could be more specific but im not at that computer right now..if anyone has any advice on this i'd greatly appreciate it. i've been searching forums for a few days(like i said) and am having no luck..my hd is 1tb, 500gb of it has windows 8.1 on it, the other 500gb i wanted to use for 2 os's:300gb for ubuntu and the other 200gb for mint(later on,after i get the other thing done)..thanks in advance for any help.

---

### Post by ian-weisser on 2015-10-21
Man, it's really hard to read all that malformatted stream-of-consciousness text. Punctuation and capitalization are *really* helpful.

First, BE SURE if you are dealing with UEFI or BIOS.
Second, BE SURE exactly which release of Ubuntu you are trying to install. It matters.
Third, don't try to install WUBI. It's both obsolete and unsupported. Just walk away from it.
Fourth, please elaborate why the normal LiveUSB method of install won't work for you. SD Cards are not the same as USB sticks. Installing an OS is much more than merely copying files across.

Dual-booting Windows and Ubuntu made a lot of sense five years ago, but is the most challenging way to install today, and hardest to support (thanks to Windows making it harder than ever). The easier way is usually to install the second OS in a VM.

---

### Post by Bucky Ball on 2015-10-21
*Thread moved to **Installation & Upgrades**.*

Welcome. You don't extract the contents of the ISO then drag and drop them to install media. That won't work. Try following one of these for a USB installer. 

UNetbootin:
unetbootin.sourceforge.net

Universal USB Installer:
[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

And try this for USB or DVD:
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Please use paragraphs in future rather than hard to read 'walls of text' (I haven't read all of your first post). Thanks. :)

DO NOT use Wubi. It is not supported any longer, even though it is available, and will NOT work with UEFI.

---

### Post by joe9450 on 2015-10-21
Ok.ill try to,i guess,leave spaces between lines so yous can understand me better.btw, i really

Doesnt matter,im getting the message out-i realize i leave out punctuation, that really doesnt matter

In here anyway..unless i was creating a technical report..alright,enough of that..i wasnt

 dragging and dropping anything..i extracted the .iso file to both abootable sd card and within
 
A separate folder on the hard drive..this "wubi" thing i could really care less about..i was

 looking for an .exe file,since i only have windows,to get the install started..if i cant use that then what 

else is there,i dont recall another .exe file in that folder.once again,im not at the machine..i leave out punctuations because i dont have much time 

when I do post,but ill give yas the spaces..dont take it the wrong way,i appreciate your help. Ill be at the machine,hell, maybe tomorrow..i just 

explained,in my original paragraph,what happened from beginning to now..and i doubt i left anything out..so i guess ill make sure its uefi

uefi. id appreciate any other help you guys can come up with.read the whole paragraph bucky ball..thanks

---

### Post by james_moore2 on 2015-10-21
I would use like YUMI or something to install the .iso file onto, (about 6gb of space needed on a flashdrive)
After installing on the flashdrive etc... boot from the usb (when booting the computer look for boot menu or settings/setup)
You can launch the installer from the menu that shows up or launch it from the live USB

---

### Post by joe9450 on 2015-10-21
alright thanks moore2,ill try usb.. i've identified the drive number of the sd slot,tried booting from it, and was brought back to the bios(uefi,whatever). my isue now is that the city's finest stole my usb (64GB) drive from me, along with my computer, and all of my cords, phones, ect.-they hooked themselves up alright and this is why i refuse to buy a usb stick..ill borrow my friends and give it a shot ..thanks

---

### Post by james_moore2 on 2015-10-21
No problem, and that really sucks.

---

