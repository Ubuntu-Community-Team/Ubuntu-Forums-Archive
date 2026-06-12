---
title: "givre_cabspace_com / ubuntu... - ntfs-3g update"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Blather_X on 2007-03-02
When I downloaded the automatic updates today (FF 2.0.0.2 and others) It times out at the end.  

I found that the "givre.cabspace.com/ubuntu..." repository was timing out.  it's been that way for 5+ hours now!  Anybody else having the same trouble?  This is where the ntfs-3g drivers are.  

Is there an update? Or is my package manager trying to connect to it  just because the link is in the repository?

I'm too new to tell if this connectivity issue is par for the course.  If not,  do I need to be looking into something?

"Please Feed The Noob!   HA!

---

### Post by toobuntu on 2007-03-07
I've noticed the same thing happening for the past week or so, so I commented the givre.cabspace and flomertens (same thing was happening) repositories out of my /etc/apt/sources.list and use the sweetsite mirror instead.  Just gksudo gedit /etc/apt/sources.list and edit the file.  Putting # in front of the line means it's a comment and the line will be ignored.

Below are sources.list entries I pulled off a website somewhere I can't remember.

# ntfs-3g Source list
# The ntfs-3g is in the universe section of ubuntu, so you'll need first to enable universe.
# If you have an NTFS removable device that you want to mount read/write, add one of this mirror in your /etc/apt/sources.list
#deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main-all
#deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main-all
# Latest version of the driver
# Add one of this mirror in your /etc/apt/sources.list to use it :
#deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main
#deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main
# GPG Key Information
# Use any one of the following Keys
# wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -
# wget [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc) -O- | sudo apt-key add -

---

