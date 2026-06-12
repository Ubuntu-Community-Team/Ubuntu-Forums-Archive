---
title: "Will a fresh install fix my problems?"
date: 2019-09-29
forum: Installation &amp; Upgrades
---

### Post by elsuzu on 2019-09-29
Hey guys!
Last year I updated my, I think Ubuntu Gnome 16, to Ubuntu 18, and had some troubles ever since. I was too stubborn to do a fresh install and now I think it's time lol 

My problems are:
[LIST]
[*]When I put the laptop in sleep mode (close it without turning it off) and turn it on again later, it's unstable and slow
[*]Audacity crashes a lot. I'd record a few songs and suddenly it reports a bug and crashes. Annoying!
[*]Firefox is very slow sometimes, but this might actually be a Firefox problem. I turned off two add-ons and it's been better since - but not great
[*]Sometimes it's all just very slow and annoying, especially when I open more than one or two apps (for example: I open Firefox, OfficeLibre, Audacity and Rhythmbox and I can hardly do anything without waiting after every step)
[*]Deja Dup never worked
[/LIST]
And last week it started reporting some problem each time I turn the computer on and all I can do is press "Report Problem", but nothing to fix it (sorry, forgot what the problem is)

Anyway, I feel like it's time for a fresh install and I have some questions.
[LIST=1]
[*]Is Ubuntu 18 still the one to go? I was quite disappointed overall by upgrading and thought about going back to Ubuntu Gnome 16, but it's probably not a smart move, is it? My disappointment might also just be due to the fact that I didn't do a fresh install (to keep my files). I just don't remember why I upgraded but there probably was a reason, so going back might not be what I really want :)
[*]I plan to save my files both on a USB stick and on Google Drive (have to do it manually since Deja Dup doesn't work), is there a better way to do it? I don't have that many files, just a lot of music and pictures and a few OfficeLibre files.
[*]Does it make sense to install both Ubuntu and Ubuntu Studio? I just read about it and while I'm nowhere near a professional singer, I do record my singing and thought maybe Ubuntu Studio might be helpful with that - but I didn't really look that much into it yet, it was just a spontaneous thought.
[/LIST]

thank you in advance :)

---

### Post by mörgæs on 2019-09-29
Yes, I think a fresh install is a good idea. 

If you are considering Ubuntu Studio then I suggest that you install Xubuntu 18.04.3 because it's the closest relative to Studio. Less additional stuff to install if you want to try Studio some day.

Only back up your music and pictures, not any configuration files. They could bring a problem along. A double backup using USB and Google Drive is a good precaution.

---

### Post by crip720 on 2019-09-29
It could, I am thinking some of the problems seem like a lack of enough memory/very old cpu.  You can install both OSs side by side, but studio is the same as ubuntu but already has install extra programs. If you think you would use most of the extras then install studio, but the extras you need can be installed on ubuntu with out having programs you will never use.  If you can it would be nice if you can give us some specs of your computer.

---

### Post by CatKiller on 2019-09-29
> **elsuzu said:**
> Does it make sense to install both Ubuntu and Ubuntu Studio? I just read about it and while I'm nowhere near a professional singer, I do record my singing and thought maybe Ubuntu Studio might be helpful with that - but I didn't really look that much into it yet, it was just a spontaneous thought.

Not really, no. It's all the same software, it's just that Studio has a different set installed by default. You can install anything that's in Studio in vanilla Ubuntu. The main difference between how they actually work is that Studio uses the lowlatency kernel (useful for JACK) and vanilla Ubuntu uses the generic kernel (marginally better performance). It's really straightforward to install the lowlatency kernel if you want it.

---

### Post by elsuzu on 2019-09-29
thanks for the advice so far! Studio is probably not a useful idea for me. I really like the Ubuntu (Gnome) Desktop and such :)

the specs for my ca. 4 year old Fujitsu AH512 are:

Intel® Core&#8482; i5-2450M CPU @ 2.50GHz × 4 
Intel® Sandybridge Mobile
4GB RAM (I just read I could upgrade to 8, would that make sense and is it easy enough to do myself?)
Ubuntu 18.04.3 LTS
GNOME 3.28.2
I used the 64bit Version, is this right?

Is this enough info?

---

### Post by cruzer001 on 2019-09-29
Your specs look good to me.  I have ran more on less :)

As  mörgæs suggested, a fresh install would be good.

If you want a gnome3 desktop that takes a little less resources, Budgie works well.

And yes, stick with 64bit no matter what you decide to run.

---

### Post by CatKiller on 2019-09-29
Definitely stick with 64-bit. 32-bit is dead.

4 GB is the minimum that you'd want for a computer for actually doing stuff on. More is always better. Any of your RAM that isn't currently being used by any applications will be used to cache files that have been used, which speeds up the next access of them. The symptoms you describe when you've got a lot of things open do sound like running out of RAM. Tools like top/htop or conky, or simply panel widgets, will let you monitor to see if that's the case.

The information that I've been able to find suggests that model can actually go up to 16 GB, and that RAM is best installed as matched pairs for dual-channel access. For laptops where you can change the RAM it's generally pretty straightforward: open a hatch (or very rarely take the whole bottom off), take out the old modules, then pop the new ones in.

Gnome is the least performant of the desktop environments, although it's getting better. KDE is good if you want a full-fat desktop environment with bells & whistles. Xfce is a popular lightweight choice, and is used by Ubuntu Studio as noted by mörgæs. Lots of people use Lubuntu (which uses LXQt) if they want something lighter than Xfce. I use Cinnamon on my laptop, and that's been fine, too. Basically, just download a bunch of install images and try out their live environments to see which you like best: everyone has their own preferences.

For your current issues, hibernation has often been a difficult problem to solve, and Audacity has often been quite crashy for a lot of people. Depending on your use case you might find Ardour to be better for you than Audacity.

Since your laptop is a little bit long in the tooth - closer to 7 years than 4, I think - it's probably due some TLC. Clearing out the vents and fans with some compressed air may help quite a lot with general stability issues.

---

### Post by elsuzu on 2019-09-30
thanks so much guys! I just checked how much a RAM upgrade to 8GB (I can't find any with 16GB) would cost and they're around 50&#8364; (the laptop itself cost 400&#8364; and it's 5,5 years old, I just checked it :) ) Do you guys think this is worth it? I'd love to use this laptop for another 5 years (or longer), but is this realistic? I'd first do a fresh install (I want to do it today) to see if my problems resolve then, but if not, would you guys upgrade the RAM for that money?
I cleaned the vents last year and they weren't even as dirty as I expected (since I had a very hairy cat then lol) but maybe I need to do it again. I specifically bought this laptop because you can open the fan without having to open the whole thing, since the cat hair was what basically killed my last laptop. But I don't think this is the issue now, I've been using it for the last two hours and it's neither warm nor loud, but still slow sometimes. Changing the RAM would probably be very easy on this laptop, then :)

I'll check out the other distros now (I read there's 25 different ones, wow!) but I just like how Ubuntu looks and works. I like the panel on the left side (that I can hide thanks to the add-ons) and that I can see all apps when I press the windows-key. I'll have to find out if that's the same with the other distros :)

---

### Post by CatKiller on 2019-09-30
Crucial's compatibility checker (which is a very useful tool even if you don't get the RAM from them) has a 16 GB kit available for €110.

I would definitely upgrade the RAM to at least 8 GB, and I'd consider 16 depending on how many heavy applications are running at once. If what's installed at the moment is a single 4 GB module you'd only need another 4 GB module to take it to 8 GB; if you've got 2 2 GB modules, you'd need 2 4 GB modules. It's worth having a look before you buy anything.

If you haven't replaced the hard drive with an SSD yet, that should also be a priority. That's the best bang-for-the-buck upgrade for general responsiveness that one can do.

My old desktop (Sandy Bridge, 16 GB RAM, SSD) should be fine for my partner's needs for a good few years for everything but heavy gaming, which is why a new desktop also exists. 3-5 more years with that laptop seems quite realistic.

---

### Post by mörgæs on 2019-09-30
Even though you like the Ubuntu / Gnome look and feel I think you should begin with a fresh install of Lubuntu, Budgie or another light Buntu. It will show how capable the present 4 GB of memory are (some of my computers only have 2).

After this you can try Ubuntu or other heavy distros for comparison. After some testing you will get a feeling for what the bottleneck is (hard- or software).

---

### Post by elsuzu on 2019-10-01
I finally re-installed Ubuntu :) I tried out Budgie first but just didn't like the look and feel. Maybe not a smart, rational decision but I just didn't want to deal with this "drastic" change. I'm a little weird with that, I know lol
But I think I'll upgrade RAM - It should help if hardware is the problem. If software was the problem, then the fresh install should work, too, right?
I've only tweaked Ubuntu to my liking, didn't do any heavier stuff. I'll try to get deja dup working right now and stuff.

If I change to a SSD, I'll have to reinstall Ubuntu again, right? Or is there any way around it? 
Since I don't much more than surfing the internet, using audacity, etc., I hope upgrading to 8GB RAM will be enough :)

---

### Post by CatKiller on 2019-10-01
> **elsuzu said:**
> 
If I change to a SSD, I'll have to reinstall Ubuntu again, right? Or is there any way around it? 
A transplant from one drive to another is possible, but requires accessing two drives simultaneously (which is often a pain with a laptop) and is potentially time-consuming. A fresh install, particularly if you've done it before, takes something like 15 minutes.

I would definitely go fresh install, personally. It's pretty straightforward to rescue those things that you're interested in keeping - settings, bookmarks, and so on - to a USB drive prior to doing the fresh install, and then copying them back afterwards.

---

### Post by elsuzu on 2019-10-01
thanks :) so I will wait with personalizing my computer and putting my files back on it, I guess. 
I'm still not 100% sure what putting a SSD in will change for me. Will it actually help performance? And are there any big differences in different SSD types? (like does it matter which company they're from?) same question for RAM :) does it make sense to just do it both? Or should I first upgrade RAM and see if that helps?

---

### Post by elsuzu on 2019-10-01
okay, I just looked and there's one 4GB RAM inside. So I can just buy another 4GB and put that in, right? Cheap and easy solution, I like that 8-)

---

### Post by CatKiller on 2019-10-01
> **elsuzu said:**
> okay, I just looked and there's one 4GB RAM inside. So I can just buy another 4GB and put that in, right? Cheap and easy solution, I like that 8-)

Yes, that should be fine. They'll run at the speed of the slowest module.

> **elsuzu said:**
> thanks :) so I will wait with personalizing my computer and putting my files back on it, I guess. 
I'm still not 100% sure what putting a SSD in will change for me. Will it actually help performance? And are there any big differences in different SSD types? (like does it matter which company they're from?) same question for RAM :) does it make sense to just do it both? Or should I first upgrade RAM and see if that helps?

Spinning rust isn't actually that bad for sustained reads of a big chunk of continuous data. What they're really bad at is random access; they need to be spun up and the head positioned to the right place to actually start reading the data that you're interested in. General day-to-day usage of a computer is completely dominated by these random uncorrelated reads; a tiny file from here, a tiny file from there. SSDs really shine at those; there's no moving parts to worry about, you just read the charge level from any cells that you're interested in. Using an SSD makes a massive difference to the general responsiveness of a computer.

There are differences in type - SLC/MLC/TLC refer to how many bit levels can be stored in each cell, with cost and ultimate lifetime going down from left-to-right. The drive itself is a bunch of flash chips and a controller, each of which need to be designed and manufactured at a certain cost/quality point. There are a bunch of reviews out there for all the popular models. Higher capacities tend to be faster, since you can read more chips in parallel that way.

For the RAM you can use Crucial's compatibility checker or just get another one the same as the one that's already in there. You'll want the speed to match, ideally. Some chips are better for overclocking or have tighter timings for marginally better performance, but they'll all work within the specifications they're listed as.

I would upgrade both the drive and the RAM, personally, but if I could only do one I'd do the SSD first and limit how much I had open at once if it was causing issues.

---

### Post by elsuzu on 2019-10-02
> Yes, that should be fine. They'll run at the speed of the slowest module.
I'm wasn't sure I understood what that means, I tried to google and I think I understand now, the RAM could have different speeds (that don't have anything to do with the GB) and if I buy a faster one than already installed it won't make a difference, but buying a slower one will, huh? lol But it also means, should I find one that's faster than the one I already have, it would make sense to buy 2x 4 from them, I think?

I'd like to buy the Crucial MX500 SSD SATA, I read that it's one of the best (for a reasonable price). I'd buy the 500GB model and think this will be enough for me, seeing as I could easily fit all my data on a 16GB usb stick :) the 1TB is almost double the price, so I think it makes sense to stick to the cheaper one with less GB, would you agree? 

for the RAM I'd like to buy the Kingston ValueRAM SO-DIMM KVR16S11S8/4 or the Crucial SO-DIMM DDR3L-1600 in 4GB. Both together would cost me a little under 100&#8364; and I think that might be a good investment. Plus I can buy it at a local shop, that's a plus in my book, too :)

---

### Post by elsuzu on 2019-10-02
I've been doing research and now decided: I'm getting both from crucial, it seems that they have quality products for reasonable prices. There might be better ones (especially SSDs) but it's an old computer and I'm using it mainly for internet, writing and Audacity, so I think I should be fine :) thanks so much for your help, I'll let you know how it all turns out

---

### Post by elsuzu on 2019-10-03
I just did it, put the SSD and the new RAM in and while I do notice the SSD helping with speed (getting my data back on the computer, installing ubuntu, all was much faster), the new RAM doesn't fit :(
I tried putting the old bar (is that what you call it?) in the slot and it didn't fit, either. 
Can you see the difference? Sorry, didn't notice the first pic was a bit blurred. Where the connecting part "splits", it should fit into the slot perfectly, with half a 1mm air between them. Work fine in the first slot. Second slot, there's a whole 1mm between them and that seems to be the problem. It's not the new bar, it worked in the other slot. Is there anything I can do now, except for getting a 8GB bar and just put that in? Or should I start a new thread for that problem?

[IMG]https://imgur.com/2cvsolE[/IMG]
[IMG]https://imgur.com/undefined[/IMG]

---

### Post by elsuzu on 2019-10-03
okay, I'm such a drama queen lol I read up on it and read that it sometimes just needs a little more force. I put the new one in the first slot and tried the old one in the second slot, et voilá! I did it, it fit and now I have 8GB RAM! I'm excited to see how that will change my computer experience, but turning it on already seems much faster.

So again, thank you guys so much for your patience and help! That's one of the reasons I love Linux, such a great community :)

---

### Post by CatKiller on 2019-10-03
Glad to hear you've got it all done.

---

