---
title: "Degraded software RAID"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by Chrus on 2013-01-05
HELP! (please)

Lost power to my PC last night and it didnt get to shut down properly. Tried to boot it up this morning and all I got after grub was a purple screen. Rebooted and got the same again. Booted into recovery mode and got a whole lot of text about mounting file systems etc, then got a "Do you wish to start the degraded RAID? [y/n]" prompt. So of course I choose Y and it "failed to start array /dev/md/0: Input/output error" and i get dropped into an initramfs prompt.

output of cat /proc/mdstat:
md1 : active raid5 sdh3[1] sdi[2] sdg3[0]
      488278016 blocks super 1.2 level 5, 512 kchunk, algorithm 2 [3/3] [UUU]
md0 : inactive sdi2 [2]
      97655226 blocks super 1.2
md3 : active raid5 sdi4[2] sdh4[1] sdg4[0]
      9762816 blocks super 1.2 level5, 512k chunk, algorithm 2 [3/3] [UUU]
md2 : active raid5 sdi5[2] sdh5[1] sdg5[0]
      3213665280 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
unused devices: <none>

So it seems to me its just md0 thats pooped itself rather than a failed drive. But seeing as 2 of the 3 drives are missing from md0, I cant repair (or even boot).

All my data is on md2, which to me looks like its still in one piece.

Is there anything I can do to get this working again?

Thanks

---

### Post by darkod on 2013-01-06
And what is md0? The root partition? /boot partition?

Have you tried if it will assemble correctly from live mode? The live cd doesn't include mdadm so you have to install it first (and do it every time you reboot since it doesn't remember it):
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should scan all disks and assemble the devices it can. See if you get lucky with md0.

Otherwise you might be in real trouble losing two partitions out of three in raid5, but you main data on md2 should be safe.

---

### Post by Chrus on 2013-01-07
Thanks Darkod

mdadm --assemble --scan gave me "not enough to start the array" - as expected.

md0 is /
md1 is /home
md2 is /data
md3 is swap

So md0 isnt overly important... its just root. If i go ahead and reinstall and recreate md0 in the process... I can mount md1+2 and all should be good??? right?

Or is there something im overlooking here?

---

### Post by darkod on 2013-01-07
Right. As long as the data on md1 and md2 is good, you can always make a clean install on md0 and attach md1 and md2 during the install, or later if you prefer.

Make sure you never tick the format box for them, otherwise, it works fine.

And of course, you will lose any customization you might have made in the OS and which is outside your /home. For settings inside /home they will be picked up since you have separate /home which won't be destroyed in the clean install.

---

### Post by Chrus on 2013-01-07
That's what I like to hear. Thought that would be the case, but its always good to get a second opinion when there's a possibility of loosing everything.

Will try it tonight and let you know how it goes.

Thanks again.

---

### Post by darkod on 2013-01-07
Depending how are you installing, with the alternate cd or the live cd by adding mdadm first, don't forget that you NEVER run mdadm --create on existing mdX devices. That will destroy the data.

You run --create only once to create the device, and for assembling only --assemble.

In this case you would need to create new md0 device and only assemble md1 and md2, if they are not assembled automatically. You don't recreate md1 and md2.

---

### Post by Chrus on 2013-01-08
Good news! Back up and running! And I still have all my data.

Had a bit of an issue with grub not wanting to boot the raid... but I showed it who's boss.

Thanks again mate

---

