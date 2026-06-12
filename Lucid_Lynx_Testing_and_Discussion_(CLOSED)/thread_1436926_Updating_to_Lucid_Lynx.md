---
title: "Updating to Lucid Lynx"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by venicequeen7706 on 2010-03-23
I don't know much at all about ubuntu, so please forgive if this is a dumb question, but when Lucid Lynx is released, can I update to that version without having to basically uninstall karmic and lose whatever personalization i have?

---

### Post by Lord Stig on 2010-03-23
You can, but the advice I've seen on the forum seems to be that an upgrade rather than a clean install can result in some problems. So not a stupid question at all!
Others are better suited to saying what kind of problems can occur, but I've done upgrades before and some worked (Karmic on my desktop), while others didn't (Jaunty on my laptop). In any case I'd back up your data.

---

### Post by OriginalName on 2010-03-23
Not maybe the best thing for a newbie but working it out once can save a *lot* of hassle come upgrade time -

When installing the system - Manually partition (there's plenty info about on the specifics of this) so you've 3 disk partitions - one for the root "\", one for your user files "\home" and one swap (usually about 1.5 to 2 times the size of your RAM). When you then proceed with the install all the system files go in "\" and all the user directories go in "\home". Desktop, specific configs for programs & documents etc all live in "\home\username" so instead of upgrading you can just do a clean install of the new version to "\" and your home directories remain untouched.

It's not super dooper easy but once you've worked it out you won't need to do it again & upgrades are easy and risk free. Plus if you bugger the system up somehow you can just do a clean install.

---

### Post by Mykk on 2010-03-23
I updated my kubuntu to lucid using the "sudo update-manager -d" and had no end of problems, thankfully i have got them all sorted out now (after a lot of pulling teeth).

...but i would seriously consider waiting a month or so for the release candidate or even the official release of lucid before using it, especially if you are new to Ubuntu.

---

### Post by Paqman on 2010-03-23
I've done loads of upgrades and never had any issues. You don't need to reinstall, but you can if you want to be sure.

If you do reinstall take a backup of your home folder, then set your user accounts up the same and copy your backup back into home. You can also get Synaptic to spit out a list of all your installed packages and reinstall them all in one go.

---

### Post by Mykk on 2010-03-23
> **Paqman said:**
> I've done loads of upgrades and never had any issues. You don't need to reinstall, but you can if you want to be sure.

If you do reinstall take a backup of your home folder, then set your user accounts up the same and copy your backup back into home. You can also get Synaptic to spit out a list of all your installed packages and reinstall them all in one go.


Yeah i must agree with Pacman, I have never had any issues upgrading to a stable release. Its always been pretty straight forward. But when you upgrade to an alpha or even a beta sometimes it causes problems (or at least it had for me, maybe I'm unlucky).

---

### Post by philinux on 2010-03-23
> **venicequeen7706 said:**
> I don't know much at all about ubuntu, so please forgive if this is a dumb question, but when Lucid Lynx is released, can I update to that version without having to basically uninstall karmic and lose whatever personalization i have?

Having /home on it's own partition makes re-installs dead easy in case the upgrade does not go well. I've had better experiences with clean installs. 
YMMV. ;)

---

### Post by Merk42 on 2010-03-23
Using the Update Manger **not** a flat reinstall is the  offically supported way.

So come April 29th (do not check immediately at midnight), just run the update manager like usual.  There will be a notification that a new distro 10.04 is available.  Let it do it's usual updating (it may take a while to download since the servers will be hammered that day) once it's all done, you'll reboot into 10.04

---

### Post by Paqman on 2010-03-23
> **Mykk said:**
> Yeah i must agree with Pacman

I should point out that I don't tend to mess about with my system much, don't compile software, and generally have a pretty normal setup. I suspect the people that run into trouble with upgrades have more complicated or customised systems than mine are.

The upgrades got a bad rep in the past because they didn't deal elegantly with extra repos, but that's pretty much been fixed now.

---

### Post by lavinog on 2010-03-23
As mentioned before, the servers will be handling a lot of traffic.
Updating the first 2 days it is released can be painfully slow. It can take a couple of hours to download all of the updates.
If you are not in a rush to update, put it off a couple of days.
Another way to update without relying on the servers is to download the alternate cd using a torrent...mount the cd, and the system should be able to do the update from the cd. (might save you a couple of hours)

---

### Post by barney385 on 2010-04-16
Excellent. I was wondering the same thing...whether to just upgrade or do a clean install, from 8.04 to 10.04.

So, after the 29th, I'll just do the upgrade. I'll do back-ups of my /home just in case.

Thx peeps...

---

### Post by florus on 2010-04-16
My experience is that upgrades work well if your original installation is working perfectly. If not, any problems seem to be magnified and a clean install is much better.

---

### Post by JoeWheeler on 2010-04-16
I've always done a clean install but if you've not got a wacky setup it should probably be fine, as long as you back up your system first then it's easy enough to find out!

---

### Post by empty_spaces on 2010-04-16
I usually go with a clean install.
I have set my computer up so that I usually alternate between 2 partitions for every release. I currently have 9.10 installed on 1 partition. When 10.04 releases, I will install it on my second partition and monitor it for a couple of weeks for any show-stoppers. This works well for me because during this initial period, I still have my fully working 9.10 install that I can continue using if anything goes wrong with 10.04.

Also, I like the "new car smell" of a fresh installation :-)

---

### Post by paynek716 on 2010-04-19
Um, brain fart here. Sorry.

---

### Post by tommynz1975 on 2010-04-19
I can't remember for the life of me but I came across in the forum a link to all the download servers for updates and could never find it again.. so one could change in the source list

If some one has the link and can post it, it would be great.

As it helps to connect to a fast server for your updates.

example previously the system was getting 48 kb/s on one server after changing it
the speed increased to 1586 kb/s and even 2100 kb/s 

Today 105mb in 1min 9s I just thought it wonderful

Take care and happy Ubuntuing Lusers :guitar:

---

### Post by cariboo on 2010-04-20
You can check for the fastest server in System->Administration->Software Sources. I'm currently getting 1200 - 2100Kbps from the main Canadian server.

---

