---
title: "same GNOME Game missisng in Lucid"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-05-05
How do you install the game 'same GNOME' in Lucid?
It was my 8 yr old nephew's favorite game. It's not in Synaptic or Ubuntu Software Center for Lucid.

---

### Post by jocko on 2010-05-06
It's still there, just had a name change and some cosmetic surgery. The new name is "Swell Foop".

---

### Post by cybrsaylr on 2010-05-06
Thanks jocko.

---

### Post by rasmith3530 on 2010-06-29
The graphics in Fell Swoop are lame compared to Same GNOME. Bring back the original, please!

---

### Post by Col-1023 on 2010-08-20
Thanks Jocko, just upgraded a laptop and found same gnome missing.

---

### Post by bkratz on 2010-10-05
Sorry about the necro--but I just found this and agree-swell foop is lame!

---

### Post by mikefreeman on 2010-10-27
Yes, Swell Foop is terrible, and crashes constantly. I want Same Gnome back!

---

### Post by Irvine_himself on 2010-11-11
I completely and totally agree, "Swell Foop" is atrocious and crashes regularly.  I found the solution is to un-install "Swell Foop" and install the "Same Gnome" deb package from karmic

[same gnome deb download link]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb")

See [this thread]("http://ubuntuforums.org/showthread.php?t=1468302") for a full discussion. 

(For me using lucid lynx, I just made sure to un-install "Swell Foop" and the "same Gnome" deb package installed with no problems)

---

### Post by robenroute on 2010-11-19
... and [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu3_amd64.deb) for all on 64-bit.

---

### Post by Irvine_himself on 2010-11-19
Since this thread is still alive I should add that if after installing the Same-Gome deb you have problems with the score then:

Run  "sudo gedit" and create three empty files in    

[LIST=1]
[*]/var/games
[/LIST]

[LIST=1]
[*]same-gnome.Small.scores
[*]same-gnome.Medium.scores
[*]same-gnome.Large.scores
[/LIST]
Then use nautilus to change the permissions of the files from "root" to to "games" and the access to read/write.

As I said, this has all been discussed in the other thread.

---

### Post by davidamcl on 2010-12-03
I agree -- please bring back Same Gnome.  It was much more visually engaging, and it didn't crash.

---

### Post by neigun on 2010-12-14
> **Irvine_himself said:**
> Since this thread is still alive I should add that if after installing the Same-Gome deb you have problems with the score then:

Run  "sudo gedit" and create three empty files in    

[LIST=1]
[*]/var/games
[/LIST]

[LIST=1]
[*]same-gome.Small.scores
[*]same-gome.Medium.scores
[*]same-gome.Large.scores
[/LIST]
Then use nautilus to change the permissions of the files from "root" to to "games" and the access to read/write.

As I said, this has all been discussed in the other thread.

The above should read as gnome and not gome.

In terms of permissions the Owner should be root and the Group games- Both should be read/write.

Others access should be read only. 

Sorry if I'm stating the obvious but as noob I thought it might be helpful.

Neil

---

### Post by Irvine_himself on 2010-12-14
Thanks, I have corrected the file paths. It was just a quick reply intended to give an overview and link to the other discussion, though this should not be an excuse for sloppiness.

---

### Post by neigun on 2010-12-15
No problem- your original post did the trick in that I now have Same Gnome with scores.

Thanks

Neil

---

### Post by Patsfriend on 2011-12-02
Hello Irvine-

The link "same gnome deb download link"  is no longer working.

I followed the other thread you have suggested but I got lost .

I am kind of a newbie... Can you seggest another location for the same gnome games download?

Very much appreciated

- Patsfriend

> **Irvine_himself said:**
> I completely and totally agree, "Swell Foop" is atrocious and crashes regularly.  I found the solution is to un-install "Swell Foop" and install the "Same Gnome" deb package from karmic

[same gnome deb download link]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb")

See [this thread]("http://ubuntuforums.org/showthread.php?t=1468302") for a full discussion. 

(For me using lucid lynx, I just made sure to un-install "Swell Foop" and the "same Gnome" deb package installed with no problems)

---

### Post by Irvine_himself on 2011-12-02
- Patsfriend


I have no idea why that link no longer works? The graphics card of my Ubuntu box recently burnt out and, for the moment,  I am reduced to using my old Xp laptop.... Oh the indignity. 

Anyway, I did a quick Google search and came up with a number of dodgy links and untrusted sites, so be warned.... you are now entering into an area where everything is suspect and constitutes a major security risk.

My best advice is to take the time to search the Debian archives for the deb package, there is a Firefox add-on "Search Site" that may help with this....  If you are lazy/stupid and do not mind taking the risk of following links offered by a total stranger,  you could try these two sites:

[http://pkgs.org/search/?keyword=same-gnome](http://pkgs.org/search/?keyword=same-gnome)  (recommended on [this]("http://forums.fedoraforum.org/showthread.php?t=262746") Fedora site)

[http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0](http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0)

Now I make no guarantee, implied or otherwise, that these sites are safe or secure and strongly recommend that you make the effort to search the [Debian archive.]("http://ubuntuforums.org/www.debian.org/")    To re-iterate, my Google search had several results that linked to sites that are known to be a security risk!

Best of luck 

Irvine.

---

### Post by Patsfriend on 2011-12-03
Irvine-

Thanks very much!
I will do the searching as recommended.


> **Irvine_himself said:**
> - Patsfriend


I have no idea why that link no longer works? The graphics card of my Ubuntu box recently burnt out and, for the moment,  I am reduced to using my old Xp laptop.... Oh the indignity. 

Anyway, I did a quick Google search and came up with a number of dodgy links and untrusted sites, so be warned.... you are now entering into an area where everything is suspect and constitutes a major security risk.

My best advice is to take the time to search the Debian archives for the deb package, there is a Firefox add-on "Search Site" that may help with this....  If you are lazy/stupid and do not mind taking the risk of following links offered by a total stranger,  you could try these two sites:

[http://pkgs.org/search/?keyword=same-gnome](http://pkgs.org/search/?keyword=same-gnome)  (recommended on [this]("http://forums.fedoraforum.org/showthread.php?t=262746") Fedora site)

[http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0](http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0)

Now I make no guarantee, implied or otherwise, that these sites are safe or secure and strongly recommend that you make the effort to search the [Debian archive.]("http://ubuntuforums.org/www.debian.org/")    To re-iterate, my Google search had several results that linked to sites that are known to be a security risk!

Best of luck 

Irvine.

---

### Post by Patsfriend on 2011-12-04
Hi Irvine-

Is there a way to get the Debian Archive to allow me in?
It will not let me search nor register either.
Just stays on the same home page.

> **Irvine_himself said:**
> - Patsfriend


I have no idea why that link no longer works? The graphics card of my Ubuntu box recently burnt out and, for the moment,  I am reduced to using my old Xp laptop.... Oh the indignity. 

Anyway, I did a quick Google search and came up with a number of dodgy links and untrusted sites, so be warned.... you are now entering into an area where everything is suspect and constitutes a major security risk.

My best advice is to take the time to search the Debian archives for the deb package, there is a Firefox add-on "Search Site" that may help with this....  If you are lazy/stupid and do not mind taking the risk of following links offered by a total stranger,  you could try these two sites:

[http://pkgs.org/search/?keyword=same-gnome](http://pkgs.org/search/?keyword=same-gnome)  (recommended on [this]("http://forums.fedoraforum.org/showthread.php?t=262746") Fedora site)

[http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0](http://www.rpmseek.com/rpm-pl/same-gnome.html?hl=com&cs=same:PN:0:0:2:0:0)

Now I make no guarantee, implied or otherwise, that these sites are safe or secure and strongly recommend that you make the effort to search the [Debian archive.]("http://ubuntuforums.org/www.debian.org/")    To re-iterate, my Google search had several results that linked to sites that are known to be a security risk!

Best of luck 

Irvine.

---

### Post by Irvine_himself on 2011-12-05
-Patsfriend

> Is there a way to get the Debian Archive to allow me in?
It will not let me search nor register either.
Just stays on the same home page.I have no idea why this is happening, there are many possible reasons. The most common are: Java Script switched off and security add-ons blocking referrals and/or re-direction requests.... etc

I usually enter the archive from a Google search page and then,  rather than use the sites search facilities, I use my search add-ons to refine the search, (see the link to my Firefox collection in my signature.)

Try googling 

```
debian "same gnome"
```or

```
debian "same-gnome.deb"
```This works for me, (remember to include the quotes!)

You have to bear in mind that you are entering fairly technical territory. What you are looking for is the highest version number of same-gnome  that you can find on the site. Idealy,  unless you are prepared to learn more than you would like to know about installing software, you want a simple package called something like "same-gnome.deb" It will probably be about 500kb to a mega byte or so.

Some warnings:

Ubuntu is derived from the Debian distro and, as a rule, you can safely use the Debian repos. Some people, (many?) include the Debian repos in their synaptic search tree and their are utilities in the Ubuntu repos dedicated to finding packages in the Debian repos. However, Ubuntu and Debian are not exactly the same and there is always a possibility of something unpleasant happening. I have never heard even a rumour of something being broken by installing from the Debian repos... But... the official line is "At your risk and peril"

The truth is that there are many reasons why it can be convenient to use the Debian archive, not least the fact that the Ubuntu archive is notoriously slow at updating to the latest versions and if you are using a utility that is undergoing rapid development, then there is real pressure to step outside the official Ubuntu repos.

Another thing that you should be aware of is that, just as in windows, all software uses shared libraries and these get updated and evolve. So the bottom line is that even though you get the "same gnome" game up and running on your Ubuntu box, eventually the underlying "lib" dependencies will evolve to the point that, (without some major tinkering,)  the game will no longer work. The beauty of Linux and open source is that this tinkering is not only possible, but some might say encouraged.

I am sorry I cannot be more helpful, but I think this is the best way to learn.

Irvine

---

