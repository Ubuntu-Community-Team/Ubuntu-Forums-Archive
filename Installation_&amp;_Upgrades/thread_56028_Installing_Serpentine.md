---
title: "Installing Serpentine"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by artmoe on 2005-08-11
Hi folks. I'm a newbie to Linux. I tried Debian out for a week and then tried Ubuntu and will stay with Ubuntu. I'm trying to still understand the concept of installing applications. I installed Serpentine today through Synaptic and it showed as, (Python-gnome2-extras) in Synaptic. I read that it doesn't come with an installer so you have to go through the terminal and type "Serpentine", to start the application. I've tried that and it doesn't start. What is it I'm doing wrong?
Also the same with Opera 8, I downloaded it to my desktop and followed the installation directions exactly and typed,"sudo dpkg -i Opera<tab>.deb but it doesn't install. Please give a newbie some assistance. Thanks.

---

### Post by Beej on 2005-08-11
Okay, I'll try and help you out. I've only been using Linux a couple of months but using synaptic is something I think I should be able  to help you come to terms with.

Have you added the extra repositories? If not check out the section in the unofficial ubuntuguide ([http://www.ubuntuguide.org/#extrarepositories)](http://www.ubuntuguide.org/#extrarepositories)). If you've not found this yet it is an excellent tool for a newbie and will get you set up with all the bits and bats you will want, DVD decoding, flash in firefox, Java, mp3 decoding etc.

After following the instructions there go back into synaptic and hit the search button. Type serpentine in the  dialogue. If installed serpentine will appear with a green box next to it. If not you should right click the box and click mark for instillation. Next click the apply button above. Another dialogue may open with a list of other programs which serpentine needs to work. just click ok and wait. 

When all is finished go to Applications> Sound and Video> Serpentine

If you can't find serpentine there go to applications> Run Applications,  and then type "serpentine" this should start the program.

When I tried I couldn't get serpentine to work. If you experience the same thing I would recomend K3b (just go to synaptic to install, will appear in applications> accessories)

Welcome to Ubuntu!

Beej.

---

### Post by Beej on 2005-08-11
Spotted this for you as well, there is a HOW TO for Opera [here](http://www.ubuntuforums.org/showthread.php?t=40449&highlight=opera) 

It doen't appear very newbie freindly, and I haven't used it myself as I'm pretty happy with firefox, but let me know if you have trouble and I'll see if I can work you through it.

---

### Post by artmoe on 2005-08-11
Thanks guys for the info. I went to do the extra repositories and I tried to figure out what was meant when I was to look for certain text and replace it with something else. It doesn't say where to look or what file to look in, so I wasn't able to add the extra repositories. But I was able to finally install Opera and get it to show up in the Application menu. Boy this Linux stuff sure is a far cry from installing apps in Windblows. But I do like the challenge of getting things to work and figuring everything out. I'll keep trying to figure out the Serpentine installation.

---

### Post by Beej on 2005-08-12
I think your having the same trouble I did when I started. In the ubuntu guide the stuff in the black box is commands you need to cut and paste in the terminal. I'll probably get slated for the comparison, but as a windows user i found it a bit reminisent of the dos prompt in the early windows days.

To open a terminal window right click on the desktop and choose "open terminal" (or whatever it is I'm at work at the mo). A window should open. copy and paste the text in the black window into the terminal, and hit return. You will be prompted for a password, enter the password you login with.

After a little busy time you should have gedit (like notepad in windows) open. You should be able to find and replace the text. 

follow steps 5 & 6.  

Give it a go, I'll keep an eye on this thread and help you out if you have more trouble.

---

