---
title: "Failed fetch on update."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by diablofatt on 2011-06-13
So when I go to update, I get: 

[B]W:Failed to fetch [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/B]

The synaptic opens up (asks for admin pw) and does nothing. Any idea's on how I can fix this? I was only able to find an article in Spanish (Or Italian.. I dunno) and I like to try and keep on my "A" game with the updates. I assumed it was a server issue on their end. Any help would be greatly appreciated. I would like to understand this better.

---

### Post by Toz on 2011-06-13
Can you post back the contents of the file /etc/apt/sources.list?

---

### Post by Old_Grey_Wolf on 2011-06-13
I checked the link for the PPA in your post, and found this, "The requested URL /danielgtaylor/ppa/ubuntu/dists/[COLOR="Red"]**jaunty**[/COLOR]/main/binary-i386/Packages was not found on this server."

You show that you are using 11.04 (Natty). If that is the case then try used an editor (vi, gedit, etc.) to remove the Jaunty reference from your sources.list file located at /etc/apt/sources.list. You could also edit the lines in the sources.list file to point to the correct Natty PPA if there is one.

If you are not using Natty (11.04) then you need to know that Jaunty (9.04) has not been supported since October 2010. I would suggest that you install a newer release of Ubuntu that is supported (supported releases are listed at [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)). For example, Lucid (10.04) is an Long-Term-Support release and will be supported until April 2013. Before you install a new release or upgrade a current release at minimum backup you /home directory.

---

### Post by diablofatt on 2011-06-17
Old_Gray_Wolf nailed it. Although I was unable to edit the file. (Root doesn't like me) 
**su -l** is the command right? (Also if anyone can guide me to a better understanding of root in Ubuntu. I'd be in your debt.)

I solved the problem by going to /etc/apt/sources.list and right clicked it and selected Open with.. 'Software Sources' clicked the 'Other Software' tab and deselected the bottom two which were my two Jaunty PPA's.

Thank you both for your time. SOLVED!

---

