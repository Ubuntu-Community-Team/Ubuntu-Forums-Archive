---
title: "Ubuntu startup hangs when gnome starts"
date: 2004-11-06
forum: Installation &amp; Upgrades
---

### Post by Jomboni on 2004-11-06
I **think**  this would be an installation issue, because I haven't managed to do anything besides getting the system installed.

Everything boots fine, gdm starts up, and the login screen appears.  When I enter my name and password, the gnome splash screen comes up and it just sits there.  Any ideas what could be causing this?

---

### Post by Jomboni on 2004-11-07
This was using the installation disc, not the live cd.  I checked around the forums and saw that a couple people recommended installing from the live cd instead, so I downloaded and burned it.  That hung on boot!  I'm not having the best luck with this :(

---

### Post by ashley_v on 2004-11-07
Same thing here.  I found out at least with me when I bring down my network interface then X will start.  If I'm connected to the net then gnome will just hang and kde does the same.  Bring down  your interface with ifconfig and then try to log in.

What gives Ubuntu?

---

### Post by ashley_v on 2004-11-08
Ok I fixed my problem.  I recommend anyone else that has this problem do the same as I did until Ubuntu has a look at that iso and see what's the matter. 

Proceed with the installation as normal all the way up to the point where it reboots your system and ask you to setup a user account.  Do that and select yes when it ask you if you want security updates from the net.  

As soon as it tries to update your system, hit CTRL C or anything to stop the process.  Switch over to a virtual console and 'sudo vi /etc/apt/sources.list'  edit that file and just uncomment out the cdrom section with a # in front of it.  Now there no more cdrom apt source, save and exit vi with :q and then 
'sudo apt-get update && sudo apt-get dist-upgrade'

At that point you should have no gnome or any other desktop so now you have to get it.  sudo apt-get kde or the same for whatever gnome components you need.

Hope that helps.  Mine has been running fine with no problems.

---

