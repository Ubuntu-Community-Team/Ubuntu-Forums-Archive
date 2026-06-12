---
title: "zero swap and crash report"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Nessa on 2008-05-29
I just finished upgrading to Heron. On first boot I got a crash report icon on the top bar but it wouldn't open. My conky configuration works but says I have zero swap. I know for a fact that I have 1 gig of swap. Partition manager does not open.

After restarting, same results. I don't see the orange Ubuntu progress bar while it loads. It's all text like the forced check after a number of boots. Crash report icon shows up but after clicking on it, it does not open up. I need help in getting the crash report open. Maybe it'll give some clues...

Please help.

---

### Post by Rallg on 2008-05-29
Did you upgrade internally (via apt-get from Terminal), or via CD? Can you boot to recovery mode? If so, from there do

sudo apt-get update && sudo apt-get upgrade

to see if your problem has already been fixed.

As for swap: Do you have the correct UUID in your fstab file? It could have changed if you re-formatted or re-partitioned, and Grub did not update. Try:

ls -l /dev/disk/by-uuid

and see if the UUID for your swap file matches its UUID in /etc/fstab.

If none of that helps, then you will probably need to post some error messages for the experts (not me) to interpret.

As for the crash message: Once in a while, I get a transitory crash while doing an update. I don't know why, but no harm done. However, the crash does not persist, as it does for you

---

### Post by Nessa on 2008-05-29
I was able to update from the terminal successfully. Sad to say that I still get the crash report. And in the text during bootup, activating swap file failed. The UUID matches in /etc/fstab though. The crash report does not open when I click the icon. The partition editor does not open as well.

So I have these main issues:

1)I get the text instead of the gui during boot up and only 1 thing fails - activating swap file.
2)Upon logging into my account, I get a crash report message but it does not open.

Weirdly, my partition for files show up as disk-1. The original disk still exists but it is empty. But I'll worry about that another time. Hopefully, someone can share more insight into this.

Thank you.

---

