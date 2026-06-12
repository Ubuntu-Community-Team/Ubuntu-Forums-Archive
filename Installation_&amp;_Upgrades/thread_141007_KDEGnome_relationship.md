---
title: "KDE/Gnome relationship"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by imhdd on 2006-03-07
I installed Ubuntu Breezy. Most of it works fine (a few problems remain - printer and sound). Then I installed Kubuntu because I have a little experience with KDE.

I now have KDE and Gnome desktops. I don't understand the relationship between the two. Does this mean that I am using Ununtu with Gnome and Kubuntu with KDE and both systems reside on my hard drive and work independently?

I'm sure the explan info is available somewhere but I haven't been able to locate  it. Thanks for any help.

---

### Post by m.musashi on 2006-03-07
Let me take a stab at this as I've just started to play with kde. Ubuntu and kubuntu are essentially the same thing except that kubuntu adds kde and some kde apps and may not include some gnome stuff (I'm not sure about that) if you install kubuntu or ubuntu you can add the desktop for the other and then at log in you can choose either. You don't need to install both (like on separate partions).

From ubuntu:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

From kubuntu it is probably install ubuntu-desktop but I have never done it from that direction.

---

### Post by m.musashi on 2006-03-07
[QUOTE=imhdd]I don't understand the relationship between the two. Does this mean that I am using Ununtu with Gnome and Kubuntu with KDE and both systems reside on my hard drive and work independently?[/QUOTE]
Sorry, should have answered this too. If you installed them on separate partitions (not recommended) they would be independent. If however, you installed one and then added the other desktop via apt-get then they are two sides of the same coin. You can access your /home from either side and you would have access to all apps (although some might not show up in the menu). I'm still new at this so I can't speak with 100% authority.

---

### Post by aysiu on 2006-03-07
If you have a red suit and a blue suit, each for separate occasions--it's still you underneath wearing the suit.

Same thing with Gnome and KDE. Same operating system. Same files. Same applications you installed. Same user. Different look and feel.

---

### Post by imhdd on 2006-03-07
Here's one reason I asked the question. I installed Ubuntu Automatix from the Gnome desktop thinking I was using Ubuntu. Downloaded several applications. Some installed and some didn't. 

Maybe that's because I was actually using Gnome with Kubuntu and should have downloaded Automatix for Kubuntu.

---

### Post by m.musashi on 2006-03-07
I can't see how that would make any difference. One thought, what apps didn't install? Mplayer, for example doesn't show up in a menu but it is installed (right?). It loads when you try and view a video in firefox. Perhaps the ones that didn't install are simply apps that run in the background or load automatically when needed rather than ones you click to run.

---

### Post by imhdd on 2006-03-07
The most desired app that didn't install is Firefox 1.5.0.1. It is in a desktop folder and I can execute it from that folder but I don't have a desktop icon for it. If I try to move or copy the icon to the desktop, it doesn't execute - it works only when it's in the folder. I stlll have the old desktop icon for the previous version, and it does execute the older Firefox when clicked.

---

### Post by Lord Illidan on 2006-03-07
[quote=imhdd]The most desired app that didn't install is Firefox 1.5.0.1. It is in a desktop folder and I can execute it from that folder but I don't have a desktop icon for it. If I try to move or copy the icon to the desktop, it doesn't execute - it works only when it's in the folder. I stlll have the old desktop icon for the previous version, and it does execute the older Firefox when clicked.[/quote]

Then right click on the icon of firefox on your desktop, and change the command to the location of the firefox exec on your harddisk.

So if you install firefox in /opt/firefox

The command will be:
/opt/firefox/firefox

Cheers!

---

### Post by m.musashi on 2006-03-07
[QUOTE=imhdd]The most desired app that didn't install is Firefox 1.5.0.1. It is in a desktop folder and I can execute it from that folder but I don't have a desktop icon for it. If I try to move or copy the icon to the desktop, it doesn't execute - it works only when it's in the folder. I stlll have the old desktop icon for the previous version, and it does execute the older Firefox when clicked.[/QUOTE]
That is odd. If you used automatix it should have set it just fine. I've used it on at least 3 computers and every time it loaded firefox and the "old" icon then launched the new firefox. I hate to sound like windows tech support but have you tried reinstalling? You might also post the question in the automatix thread. They might be able to help fix it if it's a bug of some kind.

---

### Post by imhdd on 2006-03-07
Maybe I should explain further:
I installed Ubantu Breezy. It worked fine. I wanted KDE also, so,
I installed Kubuntu with, $ sudo aptitude, instead of, $ sudo apt-get. I read that if I use aptitude I get all the Kubntu packages; if I use apt-get i get the desktop only.

I suppose if I had used apt-get I would have Gnome and KDE on Ubuntu; but using aptitude, I have Gnome and KDE on Kubuntu?? I don't know the difference in Ubuntu and Kubuntu other than the desktops. But:

On the automatix site there are two downloads to choose from: one for Ubuntu and one for Kubuntu. Using Gnome, I downloaded automatix for Ubuntu
but I guess I should have downloaded the one for Kubuntu. Ha, this is giving me a headache! 

I appreciate all the responses. Thank you.

---

### Post by m.musashi on 2006-03-07
The problem might be more my lack of understanding :). Sorry. Still, as I understand it the two flavors are just that - flavors. Whether you have kde and gnome on kubuntu or gnome and kde on ubuntu shouldn't matter. Underneath it's the same basic ice cream recipe.

I don't know why there are two different automatix. Maybe there are some minor interface differences or maybe they just don't want the kubuntu users to feel left out. Or maybe there is an issue with some difference between the two. I would still post this in the automatix thread or at least a post there linked to this one. They can probably clarify.

Easy fix? Reinstall the way you want. I've done that a good half dozen times now. It's pretty fast. Of course that is the easy way out. Digging into the problem and solving it is much more educational. Of course, your headache could be gone rather quickly (unless the same problem shows up again ](*,))

---

### Post by aysiu on 2006-03-07
[QUOTE=imhdd]
I installed Kubuntu with, $ sudo aptitude, instead of, $ sudo apt-get. I read that if I use aptitude I get all the Kubntu packages; if I use apt-get i get the desktop only.[/QUOTE] The difference between aptitude and apt-get isn't in the packages they install but how they handle those packages--read more [here](http://www.ubuntuforums.org/showthread.php?t=37736). What you're talking about is the difference between doing ```
sudo apt-get install kubuntu-desktop
``` which has all the Kubuntu packages and ```
sudo apt-get install kde-core
``` which has only the basic desktop.

---

### Post by m.musashi on 2006-03-07
I don't mean to hijack but I guess I am :)... Do you recommend aptitude over apt-get? It sounds like it should be better. What if I've been using apt-get and synaptic and then start to use aptitude? Will things get all confused or is it totally not a problem.

---

### Post by aysiu on 2006-03-07
From everything I've read, aptitude is superior to apt-get and Synaptic in terms of remembering what you have install and don't have installed. I use apt-get simply out of habit.

---

