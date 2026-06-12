---
title: "HowTo Fix Gimp [gimp-help-en] on 10.04 Lucid Lynx"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2010-06-12
Some of you may have had with issues after installing GIMP on Lucid Lynx 10.04.  Which may be directly related to "gimp-help-en", which could prevent you from installing other applications and preforming system tasks.  If so, use this method to fix it.

Process: (Terminal > $ sudo apt-get install gimp)

1. After installing Gimp go to the terminal:
sudo apt-get install -f

2. Then load up the language support application:
/usr/bin/gnome-language-selector
OR
System > Administration > Language Support

3. Then it will ask you to install the "gimp-help-en", confirm it.

4. Fix'd :)

I think this issue is directly linked to a systems with multiple languages, but I haven't been able to test this theory out yet.

Cheers,
Sugi

---

### Post by maheanuu on 2010-06-26
My problem is that no matter what I do, whether I go to download software or do the "sudo get-apt install gimp" I have nothing.  Trying to download I do not have a "download button" and on the terminal the following is what I am receiving 

maheanuu@maheanuu-laptop:~$ sudo apt-get install gimp
[sudo] password for maheanuu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gimp has no installation candidate

I sure would like to know what I am either not doing or doing wrong.  I am new at Linux, but have used Gimp for years and do NOT want to change I realize the learning curve is a little steep but so is the learning curve with Ubuntu no matter the flavor.  

Cumon Ubuntu, surely if this old DOS/Windoze user can master Gimp, you should allow me to use it...

Don't get me wrong, I think that Ubuntu is top drawer, and this is the first time I have ever grumbled about something that I don't agree with.  I had it up past my ears with Windoze and MicroShite telling me what I could do or how I could edit a page or insert a photo, etc and I hate it when windoze went out and downloaded Hell and half of Georgia, dumped it on my machine keeping me from doing things that needed doing (crappy service ADSL), then suprising me when the damn thing was downloaded by rebooting my machine....  

Please tell me that you are not headed in the direction of lil Billy and his automatons.....

---

### Post by Big_Philly on 2010-06-29
I have had no issue installing GIMP. Running it is a different story. Any kind of action in GIMP causes the entire computer to freeze and stop responding to any input. The only thing that works then is to force a shutdown by holding the power button. 

Is this the "issue after installing GIMP" you referred to, or is this something new? It may be useful to know that I use a Samsung NC20. 
Also interesting to note is that this exact same thing happened when I tried anything in Xara.

Edit: in the mean time I have tried the language support solution but this did not help.

---

### Post by maheanuu on 2010-06-29
No, Big Phillie,  I have tried to install it in 10.04 both using the terminal and also Using the "Ubuntu Software Center" in Applications.  Neither will work if I use the Gui it tells me that I need to update the Software Catalog...   and so far I have not been able to find out how to to that either...  Sort of a catch 22  You might want to subscribe to this thread though, surely there will be someone who has a lot more knowledge that we, who will probably help us both...  But again I am a dreamer, and not a pragmatist.... <grin>  I do have hope as I believe in Linux and Open Source...  Ubuntu is my choice for all the humanist reasons....

---

