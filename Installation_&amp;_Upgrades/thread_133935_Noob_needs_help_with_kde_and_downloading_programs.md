---
title: "Noob needs help with kde and downloading programs"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by myubuntuname on 2006-02-21
I was finally able to install ubuntu after a 2 week nightmare (I still don't have xp on my #1 hard drive back) ......now I need to know lots of things....

I have an AMD64 3000+ system, 1gb ram, tv tuner, d-link wifi card:

How do I get my dual monitors to function properly (nvidia 6600gt), worked throughout the entire install...but when ubuntu finally boots...only one screen works and the other has lines through it.

How do I install programs not listed in synaptic (such as VLC, wine, audacity, or cedega).....and the sister question...how do I use apt-get/sudo and learn all of the commands if I don't have access to the entire internet (see below)? Can I run a windows geneology program from wine (Legacy family tree)?....how about an Olympus audio recorder program (archive phone conversations)?

Why doesn't Firefox function properly?.....google in the searchbar doesn't work....neither does yahoo or any of the other search tools.....but typing in web pages or using my bookmarks seems to work sporadically. Mozilla is fast....but the rest of the web seems VERY slow (can't seem to download fasterfox either). The ubuntu forums flash seems to work ok...so I don't know if its a flash/java issue.

How do I install KDE 3.5 (not really liking gnome).....is amarok very cool (as good as itunes)?

How do I get my d-link wifi card to work (dwl-ag530)?....when I try to look at properties...the program quits and I can't get back in until I reboot, and it only allows me to look at my network card. 

Is there any hope of being able to use my MSI tv tuner card with remote?

MSN and yahoo in GAIM won't connect and that also means I don't know if my webcam works either (pro 4000 logitech).

Will true type fonts I had in windows work in linux?....how do I find the font folder and put them there?

I am feverishly looking all this stuff up on the forums, but it is slow going and I'm not finding much help for amd 64 users.

Please help.

---

### Post by tseliot on 2006-02-21
[QUOTE=myubuntuname]How do I install programs not listed in synaptic (such as VLC, wine, audacity, or cedega).....and the sister question...how do I use apt-get/sudo and learn all of the commands if I don't have access to the entire internet (see below)? Can I run a windows geneology program from wine (Legacy family tree)?....how about an Olympus audio recorder program (archive phone conversations)?[/QUOTE]
[COLOR="Red"]EDIT: read my whole post before doing anything![/COLOR]
First off the Search Function of this forums will be your best friend.

Cedega is not free and you have to buy it. You can use Wine which is free (Automatix can install it for you)

In this case you can try Automatix:
[http://www.ubuntuforums.org/showthread.php?t=80295]("http://www.ubuntuforums.org/showthread.php?t=80295")
Make sure you read Arnieboy's thread carefully before doing anything.

[QUOTE=myubuntuname]Why doesn't Firefox function properly?.....google in the searchbar doesn't work....neither does yahoo or any of the other search tools.....but typing in web pages or using my bookmarks seems to work sporadically. Mozilla is fast....but the rest of the web seems VERY slow (can't seem to download fasterfox either). The ubuntu forums flash seems to work ok...so I don't know if its a flash/java issue.[/QUOTE]
Java and flash can be installed by means of Automatix (they are not included in Ubuntu by default)

[QUOTE=myubuntuname]How do I install KDE 3.5 (not really liking gnome).....is amarok very cool (as good as itunes)?[/QUOTE]
Have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=126113&highlight=KDE+3.5]("http://www.ubuntuforums.org/showthread.php?t=126113&highlight=KDE+3.5")

[QUOTE=myubuntuname]How do I get my d-link wifi card to work (dwl-ag530)?....when I try to look at properties...the program quits and I can't get back in until I reboot, and it only allows me to look at my network card. [/QUOTE]
Sorry, I've never used one myself

[QUOTE=myubuntuname]Will true type fonts I had in windows work in linux?....how do I find the font folder and put them there?[/QUOTE]
Automatix will install the (default) Windows fonts for you.
For any other truetype fonts: 
Make a new directory and put only the fonts there
open Terminal and type:
cd folder_in_which_you_put_the_fonts
sudo cp * /usr/share/fonts/truetype

I guess there's an easier way to do that in KDE

[QUOTE=myubuntuname]I am feverishly looking all this stuff up on the forums, but it is slow going and I'm not finding much help for amd 64 users.[/QUOTE]
Why didn't you install Ubuntu 32bit??? There are less applications (i.e. no java and flash, ok you can get them but it can be a pain) for Ubuntu64 bit and [COLOR="Red"]I don't know if Automatix will work for you[/COLOR].

Ubuntu AMD64 is ok but it's NOT for newbies.

Even if you have an AMD64 CPU this doesn't imply that you have to install Ubuntu for AMD64. Ubuntu for x86 (or i386) will work as well.

For example I have got and AMD64 3500+ and I use Ubuntu 32bit

---

