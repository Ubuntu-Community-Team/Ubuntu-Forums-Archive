---
title: "Guidance on goals"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by chrsbrss on 2014-12-15
I've got some specifics that I want to do, not that familiar with Ubuntu Server so guidance would be greatly appreciated.  

I'm wanting to set up Ubuntu Server (14.04) to do some specific tasks.  It needs to be accessible from my two computers (lubuntu 14.04 desktop and Windows 7 laptop) both from the LAN and via Internet for uploading and downloading files - preferably in a cloud like environment so that if I put documents and photos in select files it will automatically upload to my server.  It's also going to serve as a media server using Plex media server as well as my Roku, a Bluray player that supports Plex and a couple of other devices that does not support Plex but will play MP4 videos through a server.  

I also have important documents and some family photo's/video's that I wan't to be able to sync with family members out of state, so some specific files that important documents can be uploaded and downloaded from my computer to my brothers and Mother who live out of state.  I'm wondering if it's best to bit torrent sync or just have a sync time weekly to do the documents and other files.  

The sync files for documents and pictures will need to be with a variety of different computers, mostly Windows 7 & 8, but also one brother has Ubuntu and another has Apple, plus my mother who has Windows 7 so as you see of the wide variety.  

I've currently got an older computer (Dell Optiplex 2.66 GHz Dual Core, 3 GB RAM 3 TB HDD) that I've gotten Lubuntu 14.04 and serves as a Media Server, but wan't to transform it specifically into a server capable of doing all of the above listed items, so getting some aspects of it up and running I've been able to do, but the sync and working strictly with Ubuntu Server has been providing me with some issues and headaches.  

So, 1st.  What dependencies would I need to install in the server to do what I need it to do, how do I get access to it via my local LAN (one of my biggest headaches - I can see it on my network, just can't access it with my desktop or laptop, but plays videos beautifully) using both Ubuntu and Windows 7.  Would I be best served to re-install the OS using specifically Ubuntu Server or can I just transform it into a server by uninstalling several things.

Everything is 64 Bit, if that makes any difference.  

Thanks for any guidance.

---

### Post by nerdtron on 2014-12-16
Honestly, you have a lot of requriements, but here's what I think the summary
1. You need to share files on your server, locally and publicly (internet).
2. A media server preferably PLEX.
3. You already have Lubuntu.


So,
1. For a newbie running a server and will share files through the internet, I strongly suggest don't set this manually. The internet is a scary place and it's only a matter of time before anyone attacks your server. Securing a server is a different story.
For here, it's better to use a service like dropbox if you like to share files to other people. Just install, configure and you're all set.
2. Lot's of PLEX tutorials on the net. Even on the plex website. (haven't tried it yet).
3. Lubuntu is already lightweight. No need to reinstall. Just install your needed programs like PLEX and dropbox. If you want to access the server remotely, you can setup SSH or TeamViewer.

---

### Post by chrsbrss on 2014-12-16
Yes, I've already got Plex installed on my computer and it works great, accessing it from inside my home network and via the internet is my primary difficulty.

Thanks for the reply.

---

