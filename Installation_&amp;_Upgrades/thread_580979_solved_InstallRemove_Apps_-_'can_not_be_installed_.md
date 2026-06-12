---
title: "*solved* Install/Remove Apps - 'can not be installed on your computer type (i386)'"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by kamrate on 2007-10-19
Hi all,

I just did a clean install of Edubuntu 7.10 on a Compaq Evo N1020v laptop, using a CD, and installing on a machine without Internet connectivity during the install. Everything went really well, and the system boots up and works fine. I can get to the Internet just fine now, after finding a longer cable.

When I go to Applications - Add/Remove... - then the Add/Remove Applications app starts, does a quick check, and then complains that "The list of available applications is out of date". Clicking Reload and typing my password causes the system to think a while, then download the updated lists, and then display the normal selection tree view.

When I select anything that is not already installed, I get the message "NameOfAppXYZ can not be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided not to support your computer type"

I am an expert Windows admin, but have very little experience with Ubuntu or even Linux in general so this was a bit of a challenge. Anyway, while I was typing this post I searched the web and the forums a bit, and eventually found out how to fix it. Go me!

System - Administration - Software Sources, Download From: - Other... - Select Best Server, then Choose Server.
In addition, in the Software Sources app, Ubuntu Software tab, select the appropriate check boxes for "Downloadable from the Internet".

What threw me was that they were enabled on the first laptop, but not on the second, perhaps because the second machine did not have Internet access during the install.

Hopefully this can help someone else who is stumped! The error message was not too helpful, unfortunately!

cheers

Kam

---

### Post by jatoo on 2007-10-19
Nice!

I was having the exact same problem, real frustrating, glad you solved it for me.

I have to say I've been pretty disappointed with 7.10 so far... everything worked straight away with 7.04 but not a single thing seems to have 'just worked' for this release. It's probably just me though...

---

### Post by weboutreach on 2007-10-19
Just wanted to say thanks kamrate for sharing that, seems really helpful.

Thanks,

Neil

---

### Post by crawlgsx on 2007-10-19
Thanks! Very helpful, Feeling the same way about 7.10  Considering going back to 7.04 real soon.

---

### Post by theragu40 on 2007-10-19
You are a saint for posting your solution.  You saved me (potentially) hours of frustration.  Bravo!

---

### Post by nar57981 on 2007-10-20
Thanks for the solution, I was having this problem also.

---

### Post by Vaelor on 2007-10-20
Thank you! Another problem solved :)

---

### Post by cjscouse on 2007-10-26
Thanks for the help! The only trouble that I had was that my best mirror was Artcticnetworks. Arctic networks is outta date and was giving me the trouble! LOL

So I selected the Main Server.  My download rate has improved also. Something wrong with "Canada Server", I think...

:popcorn:

---

### Post by ldisplay on 2007-10-26
> **kamrate said:**
> 
In addition, in the Software Sources app, Ubuntu Software tab, select the appropriate check boxes for "Downloadable from the Internet".
Kam

I can't seem to find that screen.


ok my bad I solved it

---

### Post by linux4909 on 2007-11-25
THANX!!!! i just followed the instructions here and it worked for me.

i've installed 7.10 4 tmes already. 

*bookmarks thread*

---

