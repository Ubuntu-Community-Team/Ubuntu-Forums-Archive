---
title: "grub error after every reboot"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by ibn4n on 2011-02-27
Edit: I think I did the procedure below a few too many times. The system finally got to the point where it just won't boot anymore even with these steps. That's ok, though. I think I'm going to use the Ubuntu Alternate installer cd and use mdadm. Thanks anyway folks!!  
 
 
Original:
 
I hope I'm not duplicating a previous thread. I really try to do my research ahead of time (I'm going on 2 months trying to get my mythbuntu system working, and this is my first post!) But now, I've reached a problem that I am not even sure how to put keywords together for. Here's the symptoms:
 
Everytime I reboot my new mythbuntu system I get the following:
 
mount: mounting /dev on /root/dev failed: Input/Output error
/init: line 326: can't open /root/dev/console: Input/Output error
[ 4.964451] Kernel panic - not syncing: Attempted to kill init!
[ 4.964486] Pid: 1, comm: init Not tainted 2.6.35-22-generic #33-Ubuntu
 
What I do then is go into the mythbuntu install cd and issue the following commands:
 
sudo mount /dev/mapper/isw_djfbiijjea_SYSTEM1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
sudo upgrade-from-grub-legacy
 
I then select 5 to install to "/dev/dm-0 (268435 MB, isw_djfbiijjea_SYSTEM)"
 
Finally, I issue a "sudo reboot"
 
I know fakeraid isn't preferable, but I couldn't figure out how to do mdadm using the mythbuntu live cd. At least with the dmraid route, I was able to get it to boot (it took me a whole weekend just to get to that point.)
 
I'm not sure what info would be useful, but here's a start:
 
- ASUS p7h57d-v evo mb
- Raid5 setup (2 logical drives in bios)
 
I'm just not sure what else is pertinent. If this was windows, I'd start pouring through procmon, but I'm a linux noob.
 
Thanks folks in advance for your support.
 
Ian

---

