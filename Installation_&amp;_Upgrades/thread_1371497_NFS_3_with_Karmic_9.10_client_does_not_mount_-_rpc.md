---
title: "NFS 3 with Karmic 9.10 client does not mount - rpc.statd issue"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by jamb on 2010-01-03
I had some weird experience related to mounting my Gutsy NFS share at boot time on my Karmic client.
This is described in this post:
[http://ubuntuforums.org/showthread.php?p=8603076#post8603076]("http://ubuntuforums.org/showthread.php?p=8603076#post8603076")

This was a work around (aka add the nolock in /etc/fstab for the mount stanza). However, what happens without nolock, 
then I must trust that rpc.statd does it's job. 
Clearly, the error message in the Karmic start does proves something is not working as expected:
> 
mountall: Event failed
mount.nfs: rpc.statd is not running but is required for remote locking.
Either use '-o nolock' to keep locks local, or start statd.
mountall: mount /home/jamb/nfs [819] terminated with status 32
mountall: Filesystem could not be mounted: /home/jamb/nfs 
 

Comparing the processes with *ps aux* on how they are started on Debian (on another PC):
> 
Debian Lenny 32-bit:                
Owner            Command            
daemon           /sbin/portmap     
statd            /sbin/rpc.statd    


With Karmic *ps aux*:
> 
Karmic 9.10 32-bit:                
Owner            Command            
daemon           portmap     
statd            rpc.statd -L   


Why this comparison, well Karmic use 2.6.31-16 kernel, use the L-option, rewritten portmap and use the *mountall* binary.
The original fstab mount stanza works as expected on Jaunty (9.04), Intrepid (8.10), Hardy (9.04), Gutsy (7.10) and Debian Lenny (5.03).

The L option in rpc.statd means (from man):
[I]       -L, --no-notify
Inhibits the running of sm-notify.  
If sm-notify is run by *some  other  script* at boot time,
there is no need for statd to start sm-notify itself.  
This can be appropriate if starting of statd needs to be delayed until it is actually need. 
In such cases sm-notify should still be run at boot time.[/I]

There is one bug report related to sm-notify here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=502122]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=502122")

Launchpad have this bug report related to mountall and NFS:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/485709]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/485709")
and NFS4
[http://https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/501678]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/501678")

Let me now if someone have had similar experiences like this, and I'm curious why we see this in Karmic but not on previous releases?
I will file this as mountall bug after having this sit here for a few more days.

---

