---
title: "Firefox 3.0 to 3.6.3.......WTF???"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Inprogress on 2010-05-03
Hello there.

Could someone please explain this and help a noob rectify it. Firstly, after countless times installing Java for Firefox, and countless times I get the error that it is installed AND that its activiate (checking it numerous times), when I get to some websites, it says my Java is either not installed or deactivated. So after days of stuggling, I upgrade my Firefox manually via a website that shows me step by step how (since I can't upgrade it inside Firefox, apparently this is because of Ubuntu....nice :?

So now its installed, 3.6.3. Only thing is, when I clink on the link in the applications menu, or the one I created in my panel, Firefox 3.0.11 opens up. And sometimes when I open a link via Evolution, 3.6.3 opens. Then sometimes it seems after I opened a link via Evolution, Firefox 3.6.3 opens. But most of the time I work with 3.0.11.

PLEASE PLEASE PLEASE help. This is irritating the living daylights out of me, and being a noob at most of linux (except when sppon fed with terminal lines) I can't get it fixed. Its driving me up the walls and one of these days my laptop out the window!

Thanks

---

### Post by P4man on 2010-05-03
Read this:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

so you understand why you cant just upgrade firefox.

manually upgrading firefox is gonna cause problems, even if you know pretty well what you are doing (and no, offense, I think you dont).

I would strongly advice to upgrade your distribution to get newer firefox and other apps. If for some reason that really isnt an option, dont use youtube howtos messing up your system, but use  a proper backport repository for firefox (and thunderbird):

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

btw, install Java using the standard repository (add/remove programs).

---

### Post by tgalati4 on 2010-05-03
You simply have two versions of firefox installed.

Open a terminal:

which firefox
locate firefox

---

### Post by TBABill on 2010-05-03
Question: Why have you chosen to do manual installs when the repositories are pretty quickly updated to new versions with update capability built into update manager? I would think the path to upgrading you have chosen is significantly more difficult than sticking to the repositories. Just curious what the rationale is.

---

### Post by Inprogress on 2010-05-03
> **P4man said:**
> Read this:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

so you understand why you cant just upgrade firefox.

manually upgrading firefox is gonna cause problems, even if you know pretty well what you are doing (and no, offense, I think you dont).

I would strongly advice to upgrade your distribution to get newer firefox and other apps. If for some reason that really isnt an option, dont use youtube howtos messing up your system, but use  a proper backport repository for firefox (and thunderbird):

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

btw, install Java using the standard repository (add/remove programs).

None taken p4man. I'm about as proficient at linux as a 80 year old fisherman with computers who returned after spending 20 years sailing around the world only stopping to grab supplies. :D

I will have to get 9.10 then....or maybe wait a tad bit and get 10.04 rahter. Will this remove all my files? Upgrading from 9.04 to 10.04? In other words, will it be a new installation?

Thanks

---

### Post by wojox on 2010-05-03
Do you have a link to the HowTo you used?

---

### Post by P4man on 2010-05-03
you cant upgrade directly from 9.04 to 10.04. You would have to upgrade to 9.10 first. Its an upgrade, not a new install, you wont lose any files, but it may also not undo all damage already done (though probably most of it).

However, one upgrade is already not always issue free, doing two is pushing your luck. Especially here, since you will also be upgrading from grub1 to grub2 and from ext3 to ext4. Pretty much guaranteed trouble. I would recommend you do a  clean install of 10.04 side by side with your current one. Test it out, once it works and you are happy with it,  move your files over and remove the old one.

---

### Post by Inprogress on 2010-05-04
> **TBABill said:**
> Question: Why have you chosen to do manual installs when the repositories are pretty quickly updated to new versions with update capability built into update manager? I would think the path to upgrading you have chosen is significantly more difficult than sticking to the repositories. Just curious what the rationale is.

Bandwidth in SA is bluddy expensive, well 3G bandwidth (can't afford ADSL yet). And the update manager has such a long list that after 20 minutes trying to select which seemingly important stuff I need to update I just left it. Then with the repository thing, there is no Firefox 3.6.3 update or version or anything, just the Firefox that is installed and the option to re-install or remove. Maybe I don't get it.

All I wanted to do was update Firefox. So in Firefox there isn't an update. So I tried Ubuntu Tweak if I remember correctly and updated Firefox or installed 3.6.3, but nothing happened. I still had 3.0.11. So I tried Add/Remove but that I explained. Synaptic I have only the idea that I have to install all the bits and pieces of an application, so I don't use that much. So via the Firefox website I think (can't remember or find the page) I found a way to update Firefox via, to my understanding update the repositories via the terminal. First the repository was loaded or updated, then the program installed.

Anyway, point is, I went the terminal route cause I couldn't figure out or find success with other methods (maybe I just missed something somewhere). And this all came from not being able to figure out how to get Java loaded/running/applying. I know I have Java installed but I can't get it running. 

I have a similar problem with Updating Inkscape, but since my Firefox experience didn't work out that succesfully, I think I will just get 10.04 and hope Inkscape 0.47 is included cause I can't get Inkscape updated. Again, I am most likely missing something. Seems nothing is that easy in Linux. 

I took a two year break from getting into linux cause I couldn't get my cellphone setup to be used as a modem. Now I'm back because of Network manager. Sometimes I wish Linux was just as simple as windows with some things. Like updating to a new software version. Download the package .exe file. Uninstall old version. Start .exe file and instal new version. Like I said, I am most likely missing something...or honestly, a lot!

Oh, and I wanted to use a light linux on my laptop. I used XFCE desktop for a while, but now I can't get my panel loaded again. With my laptop I wanted a very linux distro that uses a little resources as possible, but stiLL GUI. So I sometimes worked in XFCE, but somehow ended up loading GNOME everytime again. Not sure why come to think of it.

Well, its a learning process that isn't at the top of my list, thats probably the biggest problem.

Anyway, I will look into going to 10.04.

@ P4man: Thanks for your advice regarding moving from 9.04 to 10.04.

---

### Post by Inprogress on 2010-05-04
> **wojox said:**
> Do you have a link to the HowTo you used?

Hey Wojox. I have no idea. I tried to find it again. Its was either via the Firefox website, or I just googled it and through a forum somewhere got a link. No idea. But I remember it being explained that the repository needed to be updated/upgraded/added to first, then the app was downloaded and installed, something like "apt-get update && install" or something...or I might be thinking about me trying to update (and failing) Inkscape. But it was definitely first the repository update then the new version download and install.

Happy trails

---

### Post by P4man on 2010-05-04
> **Inprogress said:**
> 
I have a similar problem with Updating Inkscape, but since my Firefox experience didn't work out that succesfully, I think I will just get 10.04 and hope Inkscape 0.47 is included cause I can't get Inkscape updated. Again, I am most likely missing something. Seems nothing is that easy in Linux. 

Inkscape 0.47 is included in lucid.

As for it being hard, you just think like on windows where you have the OS on which you load your apps. In ubuntu, the OS and the apps are part of the distribution. Keeping it all updated is, if anything, easier once you understand how it works and you realize new apps come with the new version ubuntu as a bundled tested package. Its not impossible to upgrade individual apps, but its simply not how ubuntu is conceived. Its like trying to install Aero interface or the new windows mail from windows 7 on top of XP. It just dont work that way.

Anyway, as for bandwidth being a concern, that I imagine is annoying when using ubuntu. Consider ordering a set of ubuntu cds (for your friends too). $8 for 5 cd's:
[http://shop.canonical.com/product_info.php?products_id=625](http://shop.canonical.com/product_info.php?products_id=625)

Or request a single one for free:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Inprogress on 2010-05-04
> **P4man said:**
> Inkscape 0.47 is included in lucid.

As for it being hard, you just think like on windows where you have the OS on which you load your apps. In ubuntu, the OS and the apps are part of the distribution. Keeping it all updated is, if anything, easier once you understand how it works and you realize new apps come with the new version ubuntu as a bundled tested package. Its not impossible to upgrade individual apps, but its simply not how ubuntu is conceived. Its like trying to install Aero interface or the new windows mail from windows 7 on top of XP. It just dont work that way.

Anyway, as for bandwidth being a concern, that I imagine is annoying when using ubuntu. Consider ordering a set of ubuntu cds (for your friends too). $8 for 5 cd's:
[http://shop.canonical.com/product_info.php?products_id=625](http://shop.canonical.com/product_info.php?products_id=625)

Or request a single one for free:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Hey P4Man. Ok...that makes sense now, and I can see why it works now as well. Thanks. I get my cd's from a local chap/business. I think I will get not only the 10.04, but the whole repository discs as well this time. Its not to bad in price either. Bout R10 (that will be about, oh roughly $1 for 10.04) for the 10.04 CD, and R275 (thats about $35 for the Repository DVD's).

Yeah the internet dependability is a bit of a annoyance for me, especially when you just want to try software out and not maybe end up using it. But I have stabalised now again (always when using something new you want to try everything :D ) and I only have a small list of things that I use. I should actually uninstall the rest...or does it not really matter whether they are installed or not (that will be the standard list of software loaded with the live CD). At least that, to my knowledge is simple with Add/Remove function.

One thing I love about using Linux, is that there are hardly viruses for it. Sure as Ubuntu/Linux becomes more popular, more people will start targeting it.

Oh I remember why I stopped loading XFCE, it seems you need to configure everything. I couldn't find the volume control icon, nor could I adjust volume via the laptop "fn" key. And sometimes when I started XFCE, the volume would be mute which I was only to change my logging into GNOME and then back to XFCE. It worked quite well for me in general, but a few things just annoyed me cause it wasn't simple to figure out, like the volume thing.

Happy trails

---

### Post by P4man on 2010-05-04
> **Inprogress said:**
> Hey P4Man. Ok...that makes sense now, and I can see why it works now as well. Thanks. I get my cd's from a local chap/business. I think I will get not only the 10.04, but the whole repository discs as well this time. Its not to bad in price either. Bout R10 (that will be about, oh roughly $1 for 10.04) for the 10.04 CD, and R275 (thats about $35 for the Repository DVD's).

Looks pretty much like these prices:
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)

Not a bad idea indeed. Actually gonna do that myself, Bandwidth isnt a concern for me, but download speed is (1 mbit :( ).

---

### Post by Inprogress on 2010-05-04
> **P4man said:**
> Looks pretty much like these prices:
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)

Not a bad idea indeed. Actually gonna do that myself, Bandwidth isnt a concern for me, but download speed is (1 mbit :( ).

Excuse me, 1mbit, as in 1mb/s? I am lucky if I get 103kb/s. So really, you got it good. Usually we get about 76kb/s on 3G, many times I'm down to 2kb/s depending on the time of day when they throttle the bandwidth I think. Annoys the living daylights out of me. Bandwidth cost a hellvalot here. I can get 3GB cap per month for about, converted in Dollars: $37. And then the bandwidth is the 375 something something, the not so fast version. Last I checked I can get an un-capped ADSL line for roughly  (again converted) $500/month I think. A 10GB cap is about $150.

I heard somewhere quite some time ago that China or Japan has 100mb/s. Now that is cool. I can only dream how fast that is.

Anyway, I know we are being shafted with regards to telephone costs, cellphone costs, and internet costs in South Africa. Even bank charges. We pay the bank to take our money, and pay then to give our money bank (pay a fee for deposit - even EFT, and pay fee for withdrawal).

All the best.

---

### Post by P4man on 2010-05-04
> **Inprogress said:**
> Excuse me, 1mbit, as in 1mb/s? 

No, Mbit, not MByte. So indeed around 100 Kbyte/s actual download speed, just like you..

---

### Post by Inprogress on 2010-05-04
> **P4man said:**
> No, Mbit, not MByte. So indeed around 100 Kbyte/s actual download speed, just like you..

Now I don't feel alone anymore :D

All the best mate! Thanks for the help and advise.

---

