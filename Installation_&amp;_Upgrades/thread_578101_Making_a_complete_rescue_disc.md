---
title: "Making a complete rescue disc"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Ryokukitsune on 2007-10-16
well I'm not entirely sure to post this so here goes

I want to make a backup/install/rescue disc for my current install of Ubuntu. I currently have about 90% of stuff working correctly though I usually have to do a complete format of things when something goes horribly wrong (such as when i tried installing something and my desktop environment vanished)

since i have a lot of hardware/software installed successfully I'd like to back up the ENTIRE system (roughly about 6-7 gigs) to something that can be quickly and painlessly be restored in case of emergency, kind of like a Live CD if thats at all possible.

I have a DVD-DL so hopefully large discs won't be a problem, I'm just not sure how to set any of this stuff up. Linux up until now has been a little intimidating since most of it is done threw the terminal but I think I'm getting into the swing of things just so long as there is plenty of documentation or people to ask for help ^^;

(total drive size is without 'lost+found','media' or 'tmp')

any help will be immensely appreciated!

---

### Post by Herman on 2007-10-17
Hello Ryokukitsune,
I think the easiest and best would be [GParted -- LiveCD]("http://gparted.sourceforge.net/") because that has Partimage in it, [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
The handy thing about using Partimage in GParted LiveCD is you can make a partition to store the backup in with GParted, then use Partimage to make the backup, without even rebooting.

Here's another link about Partimage, **[Using [B]PartImage** in Ubuntu]("http://www.google.com.au/url?sa=t&ct=res&cd=6&url=http%3A%2F%2Fwww.psychocats.net%2Fubuntu%2Fpartimage&ei=bcIVR9nMJ57qgAOYyuy3Bg&usg=AFQjCNF-jBuFpDu2G7dzLiMZ7rUcC1WBUA&sig2=Y_lCGEbC17afYhY9pJYqJA")

[/B] When I do that is normally back up all the files separately to some other media  and delete them from the operating system. Then I use Partimage to back up just the empty operating system to save all the hardware and settings. Then I put back all the files I need.

Regards, Herman :)

---

