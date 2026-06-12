---
title: "Trouble with NFSv4 Server in Karmic"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Toadicus on 2009-10-18
I recently migrated to the karmic beta, as I needed some more modern mplayer and other codec builds for some work I was doing.  Everything is going well, except that my nfs server is no longer working (it was fine in jaunty).  The primary symptom is that client machines fail to mount the share by any method: fstab, manual mount, or autofs.  They don't time out; they just sit there waiting for the mount to complete and it never does.

For example: [http://pastebin.com/f4dc15e46](http://pastebin.com/f4dc15e46)

I've cleared out all of the old config files I could (I even apt-get purge'd), and I've tried turning ufw on set to allow, on set to deny with all the relevant ports open, off, and uninstalled.  Now, I think that rpc.statd might not be loading properly.  Here's a snippet of my syslog following an nfs-kernel-server restart.

```
saya:~$ sudo restart portmap && sudo restart statd && sudo /etc/init.d/nfs-kernel-server restart
portmap start/running, process 9355
statd start/running, process 10804
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ]
saya:~$ tail -n 15 /var/log/syslog
Oct 18 08:38:33 saya mountd[10688]: Caught signal 15, un-registering and exiting.
Oct 18 08:38:33 saya kernel: [87358.225609] nfsd: last server has exited, flushing export cache
Oct 18 08:38:35 saya kernel: [87359.454942] svc: failed to register lockdv1 RPC service (errno 97).
Oct 18 08:38:35 saya kernel: [87359.456979] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Oct 18 08:38:35 saya kernel: [87359.457026] NFSD: starting 90-second grace period
Oct 18 08:38:54 saya rpc.statd[10714]: Caught signal 15, un-registering and exiting.
Oct 18 08:38:54 saya sm-notify[10800]: Already notifying clients; Exiting!
Oct 18 08:38:54 saya rpc.statd[10804]: Version 1.1.6 Starting
Oct 18 08:38:54 saya rpc.statd[10804]: Flags: 
Oct 18 08:38:54 saya rpc.statd[10804]: statd running as root. chown /var/lib/nfs/sm to choose different user
Oct 18 08:38:54 saya mountd[10791]: Caught signal 15, un-registering and exiting.
Oct 18 08:38:54 saya kernel: [87378.717271] nfsd: last server has exited, flushing export cache
Oct 18 08:38:55 saya kernel: [87379.936841] svc: failed to register lockdv1 RPC service (errno 97).
Oct 18 08:38:55 saya kernel: [87379.938841] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Oct 18 08:38:55 saya kernel: [87379.938887] NFSD: starting 90-second grace period
```

I'm at something of a loss here, to be honest.  I know that karmic isn't "out" yet, so if there's another place I ought to be discussing issues with the beta, please let me know.

Thanks!

**update**
I got another computer in the mix and was able to mount the exports just fine...  It looks like it was an issue with a crashed automount on the client in question.  Thanks for looking, anyhow. :)

---

