---
title: "Ubuntu Hardy Casper Script for persistence"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-08-31
Hi,
I am attempting to fix the casper script to make my Ubuntu Hardy on USB persistence.
Despite numerous guides suggesting to drop the "mode" option during persistent disk mount, my ubuntu still boots without mounting the USB partitions.

A piece of code:

[COLOR="DarkGreen"]    # Looking for "${root_persistence}" device or file
    if [ -n "${PERSISTENT}" ]; then
        cowprobe=$(find_cow_device "${root_persistence}")
        if [ -b "${cowprobe}" ]; then
            cowdevice=${cowprobe}
            cow_fstype=$(get_fstype "${cowprobe}")
            cow_mountopt="rw,noatime"
        else
            [ "$quiet" != "y" ] && log_warning_msg "Unable to find the persistent medium"
        fi
    fi

    mount ${cowdevice} -t ${cow_fstype} -o ${cow_mountopt} /cow || panic "Can not mount $cowdevice on /cow"



I have tried a lot of times to get this working now, but to no avail.
I am really tired now.

Any help please? Why my Ubuntu Hardy still wont mount the USB drives on boot?

---

### Post by karthikb23 on 2008-08-31
Also, how can i ensure persistence?

After KDE/GNOME starts, should the 'casper-rw' mount directory be visible on my desktop?


That is precisely what is not happening.
When i check my boot logs though, it detects 'sdc1' and 'sdc2' (casper-rw), but on debugging the casper script I see that it does not mount my 'sdc2'.

Any help please??

---

### Post by DanJC on 2008-08-31
I'm not sure how to fix your problem, but you should know that Ubuntu on a Live USB will not work well, and will eventually break for one reason or another.  I know this first hand; my Live USB first forgot all of the packages (in synaptic and the add/remove program menu), then the mouse stopped working, then it couldn't load GNOME, then Ubuntu just crashed and would work at all.

---

### Post by karthikb23 on 2008-09-01
Oh god!
Dan, that sounds wierd :(

Anyways, i got the fix to my problem... just posting it. I tried my first persistence: Chainging desktop wallpaper and it works :)

But i have to see further...

Thanks!

---

### Post by gnudles on 2008-10-22
DanJC, I think I've got the same problem as yours. what's the reason for this? is it a bug?

---

