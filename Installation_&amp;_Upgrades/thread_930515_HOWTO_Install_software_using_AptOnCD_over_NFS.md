---
title: "HOWTO: Install software using AptOnCD over NFS"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2008-09-26
Good day, everyone!

I use netboot for multiple Ubuntu installations. I cannot download packages from the internet 'cause it costs my company pretty penny so the best choice was AptOnCD. But what do I do if the target PC has no CD/DVD drive and I'm too lazy to install it? It's pretty clear for Ubuntu itself, I netboot the target PC from server, but what do I do with the AptOnCD? I found the solution, it's pretty elegant:

**On Server:**
1. Install nfs-kernel-server
2. Make a folder somewhere, I will call it /path/to/my/folder
3. Copy your AptOnCD contents there
4. Edit /etc/exports file and add the following line in the end:
> /path/to/my/folder 192.168.0.0/24(ro,sync,no_subtree_check)
Do not forget to replace the subnet IP with your params if needed.
5. Restart your nfs-kernel-server with:
> sudo /etc/init.d/nfs-kernel-server restart
6. Check your NFS shares with exportfs if needed

**On Target PC:**
1. Install nfs-common. Yes, it's necessary and you'll have to fetch it from the internet (noone permits you to save it locally though, but I like the first method), but this is a small package.
2. Type the following command in terminal:
> sudo mount -t nfs 192.168.0.1:/path/to/my/folder /cdrom
Do not forget to replace the Server IP with your params if needed.
3. Open /cdrom folder to check the AptOnCD is mounted.

Now we're almost done! But there's a small thing I'd like to add: Synaptic unmounts the volume after the successful scanning. To avoid it you must mount it from terminal with the following commands:
> sudo apt-cdrom add
sudo apt-get updateIt works fine for me and I can work with the media as if it would be an ordinary CD...

Good luck to you,
Peter.

---

