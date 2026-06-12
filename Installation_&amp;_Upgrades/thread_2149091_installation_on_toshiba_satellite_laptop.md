---
title: "installation on toshiba satellite laptop"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by izzydojo on 2013-05-27
so i have a toshiba satellite laptop computer had windows 7 on it problem was it took a day to load and i hated it so i wanted to install ubuntu 12 on it for some reason it just wont install all the way without issues     its toshiba satellite c655D-s5202 system unit im installing the i386 cause i cant find out if its 64 bit or 32 bit picture below shows what happens while installing  any clue what is going on ?

---

### Post by papibe on 2013-05-27
Hi izzydojo.

Try going to text mode by pressing Ctrl+Alt+F1 or Ctrl+Alt+F2

Then login, and try this commands to get information:

To get your Ubuntu version:
```
lsb_release -a
```
To know what is your graphic card and the driver being used:
```
lspci -nnk | grep -iA2 vga
```
To check for errors on the GUI initialization process:
```
grep \(EE\) /var/log/Xorg.0.log
```
Try to get as much information as you can, and try to to post it back here.

To go back to the GUI mode press Ctrl+Alt+F7 or Ctrl+Alt+F8

Regards.

---

### Post by izzydojo on 2013-05-27
No LSB modules are available
 dist id ubuntu
 description ubuntu 12.04.2 LTS
 release  12.04
 codename  precise
 

 BGA compatible controller {003}  advacned mirco devices amd  nee ati wrestler  radeon hd 6250
 subsystem toshbia america info systesm device 1179:fde8
 kernel driver in use radeon
 

 (WW) warning (EE) error   Ni not Implemented (??) unknown
 129.737  EE failed to load module fglrx module does not exist , 0
 130.558   &#8220;&#8221;   &#8220;&#8221;&#8221;   &#8220;&#8221;    &#8220;&#8221;  same as  above

---

### Post by papibe on 2013-05-27
Thanks.

It seems you have a AMD graphic card, and you are using the radeon open source driver.

I would try to install the AMD proprietary driver.

Go into text mode again and run this commands:
```
sudo service lightdm stop

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.oldback

sudo apt-get install linux-headers-generic

sudo apt-get install fglrx fglrx-amdcccle

sudo amdconfig --initial
```
Then reboot your machine:
```
sudo reboot
```
Let us know how it goes.
Regards.

---

### Post by izzydojo on 2013-05-27
the first sudo service lightdm stop worked rest didnt its probably because the install wasnt completely done cus it keeps freezing up i skipped to the next sudo which is linux headers it only got to 9% then froze up  so im not sure

---

### Post by izzydojo on 2013-05-27
.

---

### Post by izzydojo on 2013-05-27
system is still on just screen is Blacked out cd rom is still spinning and shows the power is still on

---

### Post by izzydojo on 2013-05-27
ok so this is the only issue im seeing so far Updates Now work without it going crazy screen seems to be working good after the generic installed i downloaded the new 64 bit today but half the packages didnt take so im installing 223 updates right now the screen seems to be working good only thing that is working internet wise is wifi thank god but i do need wired to work as well any idea ? i looked in the forums for toshiba but didnt find much but ill keep searching we will see if this was the main issue hopefully ive solved the puzzle and it works good from here on out.   thanks =) any ideas on what todo with wired let me know  thanks

---

### Post by izzydojo on 2013-05-27
well after ten hours it has been determined that it can not and will not accept ubuntu it crashed so im just gonna keep that laptop as a window machine even thought i hate windows i dont think toshiba can be converted over to ubuntu thanks for the help though  i will attach the image of the kernal crash shortly

---

### Post by izzydojo on 2013-05-27
well now im offically stumped it wont even run windows 7  it installs fine no issues at all 64 bit amd but when it goes to restart it cant start back up i am beyond stumped now any ideas would be great right about now   thanks all

---

### Post by izzydojo on 2013-05-29
SOLVED!  Sold machine on craigslist  Sad pos its a Hybrid Graphics machine meaning once u uninstall a OS u can never get it back to normal without Orginal media which of course didnt come with the computer so hope no one else buys one like that 



Problem : Freezing issues  
Solved ; burn it   Cant be fixed by any means no drivers no catalyst no amd upgrades Nor Bio updates will fix this issue mostly everything on google points to Old programs that no longer exist due to updates in ubuntu and linux based systems anything that seems to work is only Temp.


=) thanks for trying all greatly appericated this learning moment lol

---

