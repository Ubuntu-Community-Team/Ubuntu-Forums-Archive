---
title: "reinstalling ubuntu wont work"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by poontuss on 2010-12-07
hi!

i havent read anything about this so i start a new topic hoping for help!
so.. reinstalling ubuntu

i have a start up usb(well, 2 acctually) and when i rebooting the computer whit the usb in it wont start with it..ive also changed in the start up meny (f12) for the computer to reboot from usb, cdrom,usb zip and blabla. still wont work.
is this normal? 
so when that didnt work i thought lets try it manually.. so i pressed the "wubi.exe" in the start up usb folder.
[[IMG]http://img163.imageshack.us/img163/1756/skrmbild2.th.png[/IMG]](http://img163.imageshack.us/i/skrmbild2.png/)

then this comes up: 
it basically say "to start live-disk you need to reboot your computer with the cd-rom in the reader. If you computer can't reboot from cd-rom the last alternative"

first altern. "reboot now"
second: "i will manually reboot later"
third: "Help me reboot from cd-rom"
[[IMG]http://img153.imageshack.us/img153/7505/skrmbild3.th.png[/IMG]](http://img153.imageshack.us/i/skrmbild3.png/)

so i press the last alternative since my computer cant reboot the "right way" then this comes up, 2 steps.
"your'e about to uninstall ubuntu"
"are you sure you want to uninstall"?

[[IMG]http://img259.imageshack.us/img259/7545/skrmbild4m.th.png[/IMG]](http://img259.imageshack.us/i/skrmbild4m.png/)
and i press uninstall then this error comes:
[[IMG]http://img844.imageshack.us/img844/2796/skrmbild5.th.png[/IMG]](http://img844.imageshack.us/i/skrmbild5.png/)

something's not right here please help me out..

why do i want to reinstall ubuntu? i'll try to explain.
when i installed my banks safetyprogram it made firefox not work..i've read around and thats happends to everyone, they start to use another webbrowser.. but i tried to install internet explorer via terminal(i used a step by step guide) and i cant find it anywhere again...
but in terminal there was "synaptic" or something..and it made a folder plop up.. and in that folder i added some commandos and i think that those commandos ****ed it up.
since then i have not been able to install or uninstall anything.. this:
[[IMG]http://img26.imageshack.us/img26/7016/skrmbild6.th.png[/IMG]](http://img26.imageshack.us/i/skrmbild6.png/)
it says: "failed to controll installed and availible programs"
"it a serius wrong in your programmagementsystem" (dont know if thats translated correct but.. i mean the system that "manage the programs")
look for broken pakages with synaptic. controll the filerights and if the file "etc/apt/sources.list" is correct. Then read about the programinformation with "sudo apt-get update" nad "sudo apt-get install -f"

i want to make those commandos i added in that folder to reset to normal thats why i want to reinstall ubuntu... if you know a better way to fix this mess help me out!
if you dont understand/ have any questions, reply and ill try to explain.

thank you for reading and also maybe for your help!

---

### Post by Mark Phelps on 2010-12-08
As far as I know, you have to run the Wubi install from INSIDE MS Windows -- the full OS, not a boot disk.  

From what you wrote, it looks like you have a boot USB and you are trying to run the Wubi installer from that. 

I don't believe that will work.

---

### Post by poontuss on 2010-12-08
yeah.. but i dont have windows and my computer wont "reboot with the usb" so i thought that might work and it didnt so..


thank you for you answer! anyone else?:popcorn:

---

