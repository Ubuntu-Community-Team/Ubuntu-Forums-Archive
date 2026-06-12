---
title: "Problem with NVIDIA GeForce4 MX440"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by dmarkv on 2007-11-28
[COLOR="Red"]Problem Solved!! My last post has the solution. About 6-8posts down.[/COLOR]

Ok I'm extremely new to Linux. I Finally got Ubuntu up and running yesterday but it only works with onboard video. I don't know what the linux lingo is, please be extremely clear and presise in directions. Step by step. I've read several posts about people who had similar but not the same. I followed their directions anyway and it didn't work.

System Specs:
Moderboard -   K9VGM-V
Integrated Graphics - Chrome 9 (all that the box says)
Video Card - NVIDIA GeForce4 MX440 APG 8x
EDIT:Distribution is Ubuntu 7.10 Gutsy (i think is the name)
The issue as title says, is with the video card. It runs fine with on-board but when I use my card it doesn't boot to desktop. It goes to the loading screen after POST but instead of going to the desktop top, it goes black. Then 4 lines appear, the last one saying
"* Checking battery state ...       [ok]"

While with onboard I went to the NVIDIA website and got the drivers for the card. I saved it to desktop and first thought was double clicky to use, since I'm a regular windows user. I didn't know where to type the command nvidia gave to run thier package, So I tried online help and left the file on desktop for time being...I'll get back to that in moment.

After research I came across people that had similar problems and tried out what people suggested.
I went to the console with ctrl+alt+F1
typed "sudu dpkg-reconfigure xserver-xorg" and followed instructions best I could but resulted in nothing. 
I found a post saying to type 
"sudu apt-get install nvidia-glx" and then type "gksudu nvidia-settings"
I did and it installed the package with first command but the second command resulted in "(gksudu:5624): Gtk-WARNING **:cannot open display" 
So I was thinking, ok since It's a GeForce4 perhaps it's legacy. So I typed 
"sudu apt-get install nvidia-gfx-legacy" and it uninstalled the first package and installed the legacy package. When I typed the second command again the same result happened.

 Now stuck again, I went back and tried the command in the console 
"sh NVIDIA-Linux-x86-96.43.01-pkg1.run" and it said 
"sh: Can't open NVIDIA-Linux-x86-96.43.01-pkg1.run"

I left console with ctrl+alt+F7 but it was just a black screen with a blinking dash. So I'm back in console on that PC and typing here on my regular.

I have no idea what to do. Any help would be appreciated. Again remember a step by step, please be clear. Feel free to use lingo but explain what it is. Took me 10 posts to realise that xserver is the system...I think. thanks again

---

### Post by twist2b on 2007-11-28
you followed the steps in the wrong order.... heres what you do.... go to recovery mode..... then this is exactly what i want you to type....

[PHP] apt-get update [/PHP]

then let it do its thing 
then type
[PHP] apt-get install nvidia-glx-new
[/PHP]
notice you missed NEW haha

then type
[PHP] dpkg-reconfigure xserver-xorg
[/PHP]
now notice that instead of a NV showing up theres a NVIDIA
select that and then follow the steps.....
ubuntu will work.... though you will need something like compiz to make the cube 100% functional..... tell me how it goes!

---

### Post by dmarkv on 2007-11-28
Ok, ran first command and it went through in like 2 seconds with a bunch of fail to update. >_<

Went ahead and tried the next anyway. Asked if I wanted to uninstall the previous and install the new one, I said Y or yes. Then it said some packages couldn't be authenticated, should I go ahead anyway, I said yes. Then it again couldn't connection to ubuntu server. So nothing happened. 

I tried last command anyway. It failed to auto detect, so I selected nvidia from the list. It asked for my card name, which imputting it resulted in asking for information such as about video card bus identifier and such. Couldnt fill that in though o.0 No idea what it is nor how to find out. I  typed "lspci" and used the number next to my card 04:04:0 if that was it. Went to the end and rebooted, same problem. I figure since first 2 failed, last wouldn't change much. 

I have internet access on that PC when I login so I don't know why it couldn't connect.

Now when we installed the OS from the start, we updated ubuntu. If that matters at the moment. 

We used the commands outside of recoverymode and command 2 did the install but alas, it ended the same way.

We did try to make it use the nvidia drivers from ubuntu with on-board and shutdown put in the nvidia card and try, still failed.

Thanks for quick response =)

---

### Post by dmarkv on 2007-11-28
just wondering, since nothin is working at the moment. When it does work, after running the xserver command, should it work immediately or should I reboot? I've been rebooting after waiting a few minutes just incase.

---

### Post by Aquilastudio.com on 2007-11-28
Just a hint: Next time you buy a computer fo linux buy it withou Nvida or Ati because they cause many problems

---

### Post by dmarkv on 2007-11-28
Ok swapped the one video card (NVIDIA GeForce4 MX440 AGP8x) for a NVIDIA GeForce4 MX440SE and put it in different PCI slot. Booted it up and it went to a configuration screen for selecting Montor type and drivers. Switched through a few resolutions and frequencies untill I found one that let me into ubuntu. So i'm on the desktop now.

Now I'm trying to get it to change drivers inside of Screen and Graphics Preferences but everytime I choose NVIDIA click test, it cancels out. When i reopen preferences it is reset to vesa drivers. If I try anything else, it shows a grey screen with X as mouse button for a moment and says test failed.

**All the PCI slots work as do the NVIDIA cards, I was just using them 3 days ago under windows. Ubuntu is being picky =)

---

### Post by dmarkv on 2007-11-28
> **Aquilastudio.com said:**
> Just a hint: Next time you buy a computer fo linux buy it withou Nvida or Ati because they cause many problems

Well this PC was built to run with windows and it did but because of a recent incident we decided to try linux. I've been wanting to for awhile anyway. If there is a list of supported video cards I would appreciate a link or suggestions of cards that are known to work easily. I saved $200+ on a new O.S. so I can go get one lol But i'll keep trying till then =) Perhaps it will help someone else later.

---

### Post by dmarkv on 2007-11-28
Got it working...or rather envy did =)

As mentioned, I moved the card to a second PCI slot. It booted to the "Screen and Graphics Preferences" Box. Only the Vesa generic drivers selection would allow us to login to ubutu. 

Came across this thread ([http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313)) and read that the poster (tseliot) was working on a program to do what I needed so I googled and found it

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

downloaded, double clicky and selected install. After install, it's listed under Applications (Top left corner of screen) in the System Tools section. Open the app and selected what I needed. This works for NVIDIA and ATI. After rebooted it loaded in. When I set Visual Effects to "Extra" and it activated the drivers completely. After reboot I could switch resolutions and had the wobbly windows and stuff :) Visual effects is located Under System-> Preference-> Appearance

Please read directions on his main page. I had changed something already that appearently he needed changed, so just incase u haven't, read all of the main page. I hope this helps. 

Also thanks for the help people I'm a bit more comfortable around the console now. And have some useful commands. Godbless. :KS

---

