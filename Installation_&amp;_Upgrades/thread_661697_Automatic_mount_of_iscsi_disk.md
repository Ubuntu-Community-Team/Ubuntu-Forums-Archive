---
title: "Automatic mount of iscsi disk"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by bricktop on 2008-01-08
Hi guys,

I have searched the forum but cant find any answers so help would be appreciated. I have a server running open-iscsi and can successfully login to the targets and they are persistent so they appear in /dev after startup.

However i need a way to mount these drives automatically, I cannot add them to /etc/fstab as iscsi only loads much later. Is there any way that I can mount these drives automatically without having to use a boot script?

---

### Post by nocturn on 2008-01-08
> **bricktop said:**
> Hi guys,

I have searched the forum but cant find any answers so help would be appreciated. I have a server running open-iscsi and can successfully login to the targets and they are persistent so they appear in /dev after startup.

However i need a way to mount these drives automatically, I cannot add them to /etc/fstab as iscsi only loads much later. Is there any way that I can mount these drives automatically without having to use a boot script?

Take a look at the automounter (autofs in synaptic/apt)

---

### Post by gtdaqua on 2008-01-29
Same help needed here! I am running 64-bit Gutsy server and am able connect successfully. All automatic. Except mounting.

I have this on my /etc/fstab

```

/dev/sdb /iscsi_disk1 auto _netdev 0 0

```

so that the volume is not loaded before network is loaded. iSCSI scripts are running ok but mounting is not happening. I have to rely on rc.local or manually do a "mount -a" to mount the devices.

Anyone?

---

### Post by gtdaqua on 2008-01-29
I found the following script [here]("http://groups.google.com/group/open-iscsi/browse_thread/thread/a835ed385d6c024d/c859e3ecf9ee3072?lnk=gst&q=fstab#c859e3ecf9ee3072")

But this is still an external script and may be not reliable. 

```

here is the iscsi-volume script :
------------------cut here -----------------------------
 #!/bin/sh
#
# chkconfig: - 99 01
# description: Mount / Umount iSCSI volume
#

#
# iSCSI volume are seen like standard scsi disk
# the rc scripts try to mount them early
# BEFORE iscsi is up,
# and more problematic, when shutdowning it try
# to umount after network is down -> crash
#
# one solution is to set the noauto flag for
# iSCSI volumes on fstab and call this script
# last on boot and early on shutdown
#

# Source function library.
if [ -f /etc/init.d/functions ] ; then
  . /etc/init.d/functions
elif [ -f /etc/rc.d/init.d/functions ] ; then
  . /etc/rc.d/init.d/functions
else
  exit 0
fi

start()
{
    RETVAL=0
    echo -n "Mouting iSCSI volumes: "
    mount /mnt/xxxx
    mount /mnt/yyyy
    return $RETVAL

}

stop()
{
    RETVAL=0
    echo -n "Unmounting iSCSI volumes: "
    umount /mnt/xxxx
    umount /mnt/yyyy
    return $RETVAL

}

restart()
{
    stop
    start

}

case "$1" in
  start)
        start
        ;;
  stop)
        stop
        ;;
  restart)
        restart
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit 0
------------------cut here -----------------------------

just put this script in /etc/init.d/iscsi-volume
and do a chkconfig -add iscsi-volume; chkconfig iscsi-volume on

TODO: it would be better to have a way to flag iscsi volumes in
/etc/fstab
and to loop automaticaly on this list. Any idea ?

Best Regards. 

```

Is nobody using iSCSI in this Ubuntu World??

---

### Post by jodeet on 2008-01-30
I'm using open-iscsi on ubuntu servers, but, alas, I'm not even as far as the person who opened this thread - my iscsi devices don't exist after a reboot.  I have to manually do an iscsiadm --login of the targets I want, and then manually mount them.

What can I do to automagically login to the target on boot-up?

---

### Post by jodeet on 2008-01-31
I solved the problem, but it's mostly a hack.  There must be a better way:

The /etc/init.d/open-iscsi script, when passed the 'start' argument, finishes up by doing an:

iscsiadm -m node --loginall=automatic

but that command had no effect, either during boot-up or afterwards.  I think the reason why was that the config files for the targets which I wanted to auto-login to, which reside under /etc/iscsi/nodes, had these attributes set:

node.startup = manual
node.conn[0].startup = manual

After I changed the value of those attributes to automatic, at least a manual invocation of :

/etc/init.d/open-iscsi starttargets

would create the devices.  However, it still would not create them on boot-up.  Because it worked manually, after a full boot-up, but not during boot-up, I guessed the problem was one of timing.  So, I delayed the target login by adding this line to /etc/rc.local:

/etc/init.d/open-iscsi starttargets

and now the devices exist automatically after boot-up.

However, the devices still aren't mounted automatically.  I've experimented with a handful of different keywords on the line in the /etc/fstab file for the desired device, but none of those variations caused the device to be mounted at boot-up.

I stuck another line in /etc/rc.local, after the starttargets line, like this:

mount -a -O _netdev

but that didn't work either.

Finally, I made it work by adding a sleep 10 after the starttargets in /etc/rc.local :

/etc/init.d/open-iscsi starttargets
sleep 10
mount -a -O _netdev

---

