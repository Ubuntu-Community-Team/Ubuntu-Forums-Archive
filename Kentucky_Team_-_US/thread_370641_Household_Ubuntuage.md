---
title: "Household Ubuntuage"
date: 2007-02-26
forum: Kentucky Team - US
---

### Post by jkeyes0 on 2007-02-26
Well, I've done it.

I made the switch for my household from WinXP to Ubuntu (at least, the portion I control...).

I switched my laptop shortly before joining this forum, and I've since reinstalled it once, to optimize partitioning. This weekend, however, I decided to move my desktop to Ubuntu as well. I had some hardships (from the ATi driver on the install disc bombing my install out, to the 8.34 ATi driver nearly disabling my system entirely) but I've overcome them all, and made the switch. I still have a copy of my old workstation in VMware format just in case I forgot something, but everything is looking good so far.

The only thing I haven't found a linux version for is a Nortel VPN client. That's the main reason I still have my WinXP vmware machine.

I'm hoping that over time I can find the time and the energy to hook up my other two workstations (one was a winxp tv pc for a while, the other is just a file server) and get them converted, and of course the wife's laptop will remain XP until I can convince her otherwise. She's getting more used to Ubuntu, but I don't think she wants it yet.

Either way, it's one more step toward total MS freedom. Hooray for open source!

---

### Post by bkingx on 2007-02-26
I'm slowly doing the same!  I have the laptop which is all ubuntu.  The wife has basically stolen that and making me use my work XP laptop.  The kids are still running 98, which is good for them because of the kiddy games out there, and the main PC is still running XP.  But w have found that since we have the laptops, we are using the main PC much less.  So I am thinking of making the switch for that one too!  And of course, the ESX server is running Linux with Ubuntu Server VM's and one 2003 vm for an IIS implementation.  The other IIS server will go away when I move the site over to drupal or some other CMS.

---

### Post by jkeyes0 on 2007-02-26
Of course, I jinxed myself...

I rebooted on my way to bed last night, and didn't bother to watch it start back up. I stayed home from work today, and when I came down, I found that it was sitting at the Ubuntu loading screen (with the scrolling bar across the bottom) with a green stripe across the middle, locked up.

I rebooted, nothing. I tried recovery mode, nothing. I replaced my xorg.conf file, nothing. FInally, after about 4 reboots, in recovery mode, my system decided to do an fsck on /dev/hda2. I'v been sitting here ever since watching it spout off about Buffer I/O errors on hda2. :(

At this point, I'm loading up the livecd to see if it can fsck a little easier. If not, I'll pull that drive out and work from my sata drives alone. Fun, fun day.

---

### Post by montgoej on 2007-02-26
I've switched completely to Linux(Ubuntu and Sabayon specifically) with all the computers I control, although my parents still have computers with Windows XP, but that is gonna(hopefully) change soon.  I've talked my mom into at least letting me install Ubuntu on her old computer when we get a new one,  and my dad is gonna let me install it on his old one, once he buys a new computer.  The toughest part for me was the fact that I use stuff like Dreamweaver, but I've gotten over that by now.
~Jordan Montgomery

---

### Post by kambrik on 2007-02-27
I'm glad to hear the ubuntu movement is catching on for alot of people.  Me personally i was trying other versions of linux on and off for the past couple of years, starting with mandrake, and then slackware, and then i came across ubuntu.  I installed on my sony vaio laptop (switching from winxp) and i have loved it ever since.  I have actually installed it on my kids desktop computer as well, and even working on the server edition at my work.  Once my new computer arrives i am taking my current desktop computer and installing server edition on it as well and making it a domain/file server.  I have told alot of people about ubuntu and i would use it over any other distribution.

---

### Post by jkeyes0 on 2007-02-28
After some more hardships (just a run of bad luck) I got Ubuntu reinstalled on my desktop system with little to no file loss. I hadn't put anything on my /home partition yet other than .deb files, and those I can download again.

I've also installed Ubuntu 6.06 LTS on my file server. I might just reinstall it sometime soon though as a 6.10 server, because I've never installed the server version and would like to see how it goes. Now that I know how to set up SSH, I really don't need the gui. I've got one more desktop machine that I might take to Ubuntu, but it's not been turned on in several months, so there's no rush on that. The wife's laptop is the only thing really left with XP at this point, and she's adamant about not switching it. It's a 400mhz, 256mb ram machine, so it might only be friendly with Xubuntu anyway, and I don't think she'd care for that interface.

---

### Post by kambrik on 2007-02-28
jkeyes0 - i would recommend getting the server edition and playing around with it.  OpenSSH server/Client is very easy to install on it and you will be up and going with that and samba (if you wish) in no time.

---

### Post by jkeyes0 on 2007-02-28
Well, I've got openssh server on my 6.06 fileserver at the moment, it's just a desktop install instead of a server install. I might download the 6.10 server disc and reinstall for fun, though. 600gb of storage space empty, and I need to find something to do with it.

---

### Post by kambrik on 2007-02-28
Yeah you do have alot of room to play with there... Also check this link out this might be a better use of your HD space. 

[http://plutohome.com/index.php]("http://plutohome.com/index.php")

You can use your own hardware etc...

---

### Post by srwalter on 2007-03-01
My girlfriend, mom, and sister have been using Linux for a long time now.  They're currently using Ubuntu, but used FC3/4 before that, and Debian before that.  The last windows machine we had was a Packard Bell 120MHz.  (They all love Ubuntu, too)

---

### Post by jkeyes0 on 2007-03-01
I'm really considering loading Edubuntu-desktop onto my laptop and showing it to the family. My brother has 3 kids now (8, 4, and <1) and I think it would be a great addition to at least my parents' computer.

Actually, no. My parents can't go to Ubuntu, because my mom is an accountant, and with no readily available tax software, it just won't work... hmm, lots to think about.

---

### Post by JarG0n on 2007-03-01
> **jkeyes0 said:**
> I'm really considering loading Edubuntu-desktop onto my laptop and showing it to the family. My brother has 3 kids now (8, 4, and <1) and I think it would be a great addition to at least my parents' computer.

Actually, no. My parents can't go to Ubuntu, because my mom is an accountant, and with no readily available tax software, it just won't work... hmm, lots to think about.

Have they considered using WINE for their Windows based tax software?

---

### Post by Koji-Murasame on 2007-03-01
> **JarG0n said:**
> Have they considered using WINE for their Windows based tax software?

Or someone suggested earlier in IRC, making a windows virtual machine (on VMware or the like) to run the software.

---

### Post by JarG0n on 2007-03-01
> **Koji-Murasame said:**
> Or someone suggested earlier in IRC, making a windows virtual machine (on VMware or the like) to run the software.

Yeah, that would work great for things that don't work well in WINE I believe.  But then you have to justify to newbies why they would even want to go through the hassle (overhead) of running a VM.  The reasons are obvious to us, however to potential new users, it may be frightening and not cost justified in terms of learning a new OS and supporting software (VM).

I think showing new users the video in the sticky thread I posted will close the deal quite nicely with new users coming from Microshaft.  Mark outlines the benefits quite well, in a format that people like, video!

---

### Post by jkeyes0 on 2007-03-01
> **JarG0n said:**
> Yeah, that would work great for things that don't work well in WINE I believe.  But then you have to justify to newbies why they would even want to go through the hassle (overhead) of running a VM.  The reasons are obvious to us, however to potential new users, it may be frightening and not cost justified in terms of learning a new OS and supporting software (VM).

I think showing new users the video in the sticky thread I posted will close the deal quite nicely with new users coming from Microshaft.  Mark outlines the benefits quite well, in a format that people like, video!

I'm not sure the video would do much for my parents, but if I could convince them that they won't lose any of their data (from a VMware machine)

I think what I'll do is take my Edgy laptop in when I go for my dad's birthday next weekend, and see what they think of it. I'll install the Edubuntu desktop so they can see all the kids apps, and try to show them how easy it can be to work with. They're mostly illiterate when it comes to Windows as it is, so it wouldn't be that much of a stretch to switch, I'd just have to remain their administrator like I am now.

---

### Post by JarG0n on 2007-03-01
It's really amazing how glued people are to OS aesthetics, including myself.

---

### Post by Condoulo on 2007-03-08
I'm the only Ubuntu user in the house.... for now. My Dad plans to switch soon on his personal computer, my Dads work computer will have some form of Linux, my younger brother wants to switch but his wireless card has many troubles. Not sure about my Mom. My other younger Brother has Windowblinds and doesn't want to give up his theme, so thats gonna be hard,

---

### Post by jkeyes0 on 2007-03-09
I talked to my dad last night about Ubuntu, and he said "what's different about that?"

I told him he uses Windows, and that I used to use Windows, and he, of course, said "What's Windows?".

I think if I took a copy of Kubuntu there with the "Bliss" background from XP (or the picture of my niece that he keeps as his background) he'd never notice the difference. Give him an "Internet" icon, and he'd just chug right along.

Mom, on the other hand, is an accountant, and needs TurboTax to work. VMware, here we come. :)

---

### Post by Condoulo on 2007-03-09
I got a question... where do you get VMware?

---

### Post by etank on 2007-03-09
[http://www.vmware.com/](http://www.vmware.com/). You could also look into [http://www.virtualbox.org/](http://www.virtualbox.org/).

---

### Post by jkeyes0 on 2007-03-09
> **Condoulo said:**
> I got a question... where do you get VMware?

[http://www.vmware.com/products/free_virtualization.html](http://www.vmware.com/products/free_virtualization.html)

---

### Post by Condoulo on 2007-03-09
Thanks. :)

I downloaded the Tarball, but I have no idea how to install it.

---

### Post by bkingx on 2007-03-10
I really like virtualbox.  It seems to run a bit leaner than vmware.

---

### Post by Condoulo on 2007-03-10
What are the differences between the two? Or should I ask, which one runs faster?

---

### Post by bkingx on 2007-03-10
Well, IMO, Virtualbox runs faster.  It seems to use less resources and is pretty responsive.  But both are nice products.  Try them both and see which one you like.

---

### Post by etank on 2007-03-10
> What are the differences between the two? Or should I ask, which one runs faster?

I think that Virtualbox is a little easier to install too.  You can download the .deb file and then use gdebi to install it. Or you could do a ```
sudo dpkg -i **filename.deb**
```Once that is done then just add your user to the vbox group.

---

### Post by Condoulo on 2007-03-10
Thanks. :)

---

### Post by redoscar3 on 2007-03-11
I am pretty much a household user of Linux.  To be honest, my Ubuntu machine is the Acer laptop, and that's a pretty recent install.  My primary desktop box is still running a tricked out Mepis 3.3 install.  It runs Quicken 2002 under Crossover Office, and Win 98 under Win4Lin.  This way I can do pretty much anything I need with it.  But in the end, I still mostly just use the Linux software and Quicken.  I rarely do anything in Win4Lin.

But I like Ubuntu on the laptop.  Wireless using ndiswrapper works wonderfully.  Ubuntu networks to my file and print servers with no problems.  And I love the ease of updates in Ubuntu as well as the great community around it.  Ubuntu just takes a lot of the burden out of getting Linux installed for the desktop user.

Red

---

### Post by Zuph on 2007-03-13
> **Condoulo said:**
> What are the differences between the two? Or should I ask, which one runs faster?

The difference between the two?

Not much.  The performance difference is maybe a few percent, even less if you're not using a GUI.  It all comes out in the wash.

In my opinion, VMWare is a little more stable a product, with more solid support and decidedly better remote-management utilities.

For the free products, VMWare and VirtualBox are about the same.  For VMWare's enterprise stuff, though?  They blow everything, with the possible exception of a REALLY REALLY good Xen setup, right out of the water.

---

### Post by Condoulo on 2007-03-13
Whoot. Success! I got my Brother's SWL-2300U working. He is now using Ubuntu as his main OS now.
Sad thing is, all it took was ndiswrapper. Dunno why I spent so many months trying to get it to work.... but then again, there are pretty much no good guides for the SWL-2300U out there.

---

### Post by srwalter on 2007-03-14
Awesome!  I'm glad you were able to get the card functioning.

---

### Post by Condoulo on 2007-03-16
After showing my other younger brother KDE, he may consider dual booting.

---

### Post by X-626 on 2007-03-17
After having a *ton* of trouble with a few things in XP (even **after** a clean install, the same thing happened), I was finally able to convince my family into letting me wipe XP and replace it with Ubuntu!  (that was actually a few days ago)  I'm happy I no longer have to try to fix it here (though, I still have to use/fix it at school and everywhere else I go).

---

