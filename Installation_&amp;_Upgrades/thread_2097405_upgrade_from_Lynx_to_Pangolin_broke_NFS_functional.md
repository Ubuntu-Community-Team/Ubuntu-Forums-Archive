---
title: "upgrade from Lynx to Pangolin broke NFS functionality"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by mrluohua on 2012-12-23
Hi !  Love ubuntu, been using it for years and years.

My setup was Lucid Lynx sharing nfs out to an old TVIX media-player connected to my TV.

I NFS shared out /extra -- and under extra I would mount usb drives, sata drives, and esata drives suchly:

/extra
---> store1/
---> store2/
---> store3/

each storeX being it's own mount.  Now I used nfs-user-server and everything worked well.

Upgrading to Precise Pangolin (seemingly successful upgrade!!) seems to have discontinued support of nfs-user-server in favor of nfs-kernel-server.

Now when I view shares on my TVIX box, /extra/store1/ and all other storeX/ sub-mounted shares are now 'empty'.  The contents aren't shared out.  I can see media that is directly in /extra/ but I have all my media in my various storeX/ mounts.

After googling for quite a while, some say "thats how it's suppose to work".  Others say "play with nohide and/or crossmnt".  No matter how I've tried to get my media center back working, it just won't show media (content) in the sub-mounted directories.  

1) does anyone know how to make nfs share out mounts that are under the main share?
2) does anyone know how/where I can download binaries or source for nfs-user-server that will work on Precise Pangolin?

Thanks so much for any help or insight !

mrLuohua

p.s. one caveat: my TVIX media player is old and no longer supported; it might not understand newer NFS

---

### Post by mrluohua on 2012-12-23
If it helps, my /etc/exports like:

```
/extra           10.10.10.0/255.255.255.0(rw,sync,all_squash,anonuid=9999,anongid=9999)
```

Additionally, under nfs_user_server (under Lucid Lynx) this setup worked fine for years.  It only broke (stopped sharing child mounts) after the upgreade to Pangolin and nfs_kernel_server.

---

