---
title: "how to disable services /w upstart?"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by SilatDo on 2012-06-27
I've just installed 12.04.  After rebooting, the bootup stalls at
"starting cups printing spooler/server"

I removed  /etc/init.d/cups , to no avail.

Could you please tell me, how to disable services/demons from being initialized?

---

### Post by VMC on 2012-06-27
Have a looked into ```
man cupsd.conf
```

---

### Post by SilatDo on 2012-06-27
> **VMC said:**
> Have a looked into ```
man cupsd.conf
```

Why?  How's "man cupsd.conf" gonna give me an insight on the intricacies of upstart?  Please elaborate.

---

### Post by VMC on 2012-06-27
> **SilatDo said:**
> Why?  How's "man cupsd.conf" gonna give me an insight on the intricacies of upstart?  Please elaborate.

Upstart?! I thought you wanted to stop cups.

edit: I got confused with your first post. The message "starting cups printing spooler/server" is the last message, and then it hangs?

edit2: This "starting cups printing spooler/server" message may be a red herring. Reading some other post with similar message, it was something else causing the problem. Its just the "cups" message is the last thing seen. Check you var log files for any clues.

---

### Post by SilatDo on 2012-06-28
@VMC: you're right. It seemingly has nothing to do with cups.

I'll explain what I've done so so far:
As it seemed to me that cups was stalling upstart, I followed these instructions:
[http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting](http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting)
didn't help.  Or rather: it probably worked, but upstart still stalled somewhere, but I don't remember where.  So I kept suspecting cups.

Therefore chrooted into it and did
 # apt-get --purge remove cups

After rebooting, network-manager seemed to stall upstart, so I did
 # apt-get --purge remove network-manager
Then the same with bluetooth
 # apt-get --purge remove bluez

Now, upstart doesn't seem to do anything at all.  The bootup stalls at
 > /dev/sda2: clean, 151978/1222992 files, 642641/4882432 blocks

So I followed these instructions:
[http://upstart.ubuntu.com/wiki/Debugging](http://upstart.ubuntu.com/wiki/Debugging)

I added "--verbose" to the kernel options, and tried to make upstart give some feedback
> # cd /etc/init/
 # for i in *; do sed -i '/^exec.*/i echo "This is exec $0."' $i ;done
 # for i in *; do sed -i '/^script$/a echo "This is script $0."' $i ;done
 # for i in *; do sed -i '/^pre-start script$/a echo "This is pre-start script $0."' $i ;done


Still, I get no output from upstart.
BTW: redirecting the output of echo to a file didn't work, because mounting the kernel read-write
 > kernel /vmlinuz root=/dev/sda2 rw --verbose
didn't work.

/var/log/dmesg is still empty.

Any ideas?  Thanks.

---

### Post by VMC on 2012-06-28
Read the [7th post]("http://forums.debian.net/viewtopic.php?f=30&t=79439") from this guys problem, to get an idea of the scope of our problem.

You didn't say how long you left it hanging - 1 minute, 5 minutes. The reason I asked is one time I also thought my boot was hanging, but after 5 minutes it booted. so I then checked log files to find help.

In the above link, it was suggested to run [bootinfoscript]("http://sourceforge.net/projects/bootinfoscript/"). It may not seen related, but its worth a try to add various options to linux line, such as "nomodeset".

---

### Post by SilatDo on 2012-06-29
I gave up on pursuing this.  I reinstalled with the alternate-CD, instead of the live-CD, and now it boots through.
Thanks for your support, though, especially @VMC.

---

