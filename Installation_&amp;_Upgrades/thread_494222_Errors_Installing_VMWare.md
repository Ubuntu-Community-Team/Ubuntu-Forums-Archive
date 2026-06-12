---
title: "Errors Installing VMWare"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by evolving_monkey on 2007-07-06
Hello all,

I am trying to install VMWare to run XP in Linux. When I try to install vmplayer it says that it conflicts with libdbus-1-2 and when I try to install vmserver it says that there is a previous intallation and I need to remove it by running vmware-uninstall.pl. I have never have never installed any vmware to the best of my knowledge.

The problem is that if I remove libdbus-1-2 it will also remove firestarter and many other programs that I don not want to loose. When I try to run vmware-uninstall.pl nothing happens and it doesn't show up in the list of known applications.

Any suggestions would be great

Thank you for your time

---

### Post by evolving_monkey on 2007-07-06
O.K, I was able to install VMWare player through synaptic. It resolved the conflicts. The problem now is taht when I try to install vmware-server it that it must remove:

(1) vmware-player
(2) vmware-player-kernal-modules
(3) vmware-player-kernal-modules 2.6.20-16

I thought I need both to install windows in Ubuntu so I am a bit confused. Although I am looking at two different install methods. One with the player and server and one with just the player.

Not sure what to do next.

Thank for your time

---

### Post by dabl on 2007-07-06
If you just want to run XP in Linux, which is what it says in the original post, then you only need VMWare Player.  Why are you trying to install VMWare Server?

---

### Post by evolving_monkey on 2007-07-07
Actually I found a guide that explains it pretty well. I do not have to install vmsever. Thank you dabl.

[http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:mode](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:mode)

Everything works The only problem is that it doesn't seem to recognize where my DVD drives are. In the post it mentions emailing him with where they are and he will send you a corrected file. I might do that but I have been trying to figure out how to do it myself first.

As to why I was trying to install VMServe, I found a how-to that was really pretty off. The one above got me there.

If anyone can explain how to edit the winxppro.vmx file or where I might find a guide that would be greatly appreciated. I'm going to keep hunting.

Thanks

---

### Post by evolving_monkey on 2007-07-07
Dabl, thank you again for the website. It cleared up how to get started and pointed me in the direction to get the rest. I have vmware player installed and seemingly working. I was able to load vmware server on an old system with  Windows server 2000 on it so I can edit the .vmx file. So far that seems pretty straight forward. 

I was able to set the cdroms to auto detect and that did the trick with that problem. On the Ubuntu machine with VNWare Player. The screen went black and then went in to the blue windows XP installation. I didn't actually install XP because I wanted to do some more investigating first. But it was a successful first test. Very encouraging.

I am going to do some more reading on how to set up the hard drives, memory, sound card and stuff like that. I will probably only go with what is necessary for now but I haven't quite defined that yet. Any suggestions on set up and editing the .vmx file would be greatly appreciated. 

Oh, and by the way. I was kidding about not being a 'brick to the head" noob in the other post. I typed it with a smile but when I read over it again it looked like it might have come off a bit snotty..I am truly appreciative but I think sometime my sense of humour doesn't make it the way it was intended from my keyboard to the readers face. So if that came off wrong...my apologies.

Also, I didn't actually mean to start talking about this topic in two different posts. I was strung out on caffeine trying to bounce around on about 30 different posts started by others trying to figure things out. I got a bit confused and lost track. I now have sleep and clarity on my side. For now anyway...... 

Again, thank you very much dabl. That was an excellent resource.

---

