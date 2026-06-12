---
title: "Ubuntu 10.10 - Issue with grub on re-boot from hibernate"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by tobiz on 2011-11-14
When I restart my 10.10 system by Wake-on LAN or RTC Alarm after hibernation via rtcwake -m disk {some time option} it resumes correctly the first time this is done after a cold start but if then put into hibernation again and restarted it drops into the grub menu to select which OS to run.  This seems to be some sort of grub issue which is controlled by the /etc/grub.d/00_header script which at the end says:
"cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF"

It looks like after the first restart from hibernation something is set such that if repeated timeout is set to -1 and hence grub drops into recovery mode.

One solution would be to change this part of the script but better to know why it's happening and fix that if possible.  What's causing the problem?  Just for info, this doesn't happen on 8.10.

---

### Post by tobiz on 2011-11-14
I changed
set timeout=-1
to
set timeout=${2}

The script snippet from the earlier post was from 10.04, in 10.10 it seems set timeout=${GRUB_TIMEOUT} is now
timeout=${2} 

This as suspected solves the problem but I'd still like to know why it happens and the 'right' way to fix it.  Is this an issue for the grub/ubuntu developers?

---

