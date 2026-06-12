---
title: "Rufus iso burner2.12 grub error?"
date: 2024-04-28
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2024-04-28
Hello having an issue burning a Kubuntu 24.04 install iso. It shows an error page with image uses Grub 2.12 but only includes files for Grub 2.06 error. Will burning the ios as is work?

---

### Post by TheFu on 2024-04-30
I haven't used rufus in 8+ yrs. At the time, it was having issues and the project wasn't updated for the new releases I cared about.

But we don't actually need any special program to create a bootable flash drive on any Linux system. We can use 'cp' to do it.

```
sudo     cp      /tmp/path/to/ubuntu-24.04.desktop.iso   /dev/sdz
```

Just be 100% certain you get the correct device for the whole flash storage device, /dev/sdz in my example.  Get that wrong and it will be a very bad day.  But it really saves hunting down the current, popular, ISO burning, program.  cp  (or any other program that won't molest the bytes being moved from A ---> B) is easy, fast, on every system.

---

### Post by guiverc on 2024-04-30
If you're using apps (such as rufus) to change the grub version; you're actually re-formatting the ISO during write to media.

The ISOs are *Quality Assurance* tested using no-format-change, ie. a simple *clone* of the ISO to the install media.

If you modify/reformat an ISO, whether or not it works, will depend on what ISO you're using, plus what options you actually used.  The version of rufus can matter too, if the ISO is newer than 20.04.

There can be benefits to reformats though; eg. I have a box with a *firmware issue* (bug!) that causes the boot of an ISO to take 10 minutes... reformatting the ISO can bypass this slow boot and save myself >8 mins of boot time, HOWEVER the reformat will also prevent that thumb-drive from booting on other boxes... Myself; I don't do that, just *clone* ISOs to media so it'll work on all hardware, even if I have to wait >10 minutes to boot on a single *annoying* device.

*Please not the BUG is not in Ubuntu or any software.. but in the machine firmware itself, the maker just never fixed it... as is the case for a number of different make/models.*

---

### Post by Rubi1200 on 2024-04-30
You have two options:

1. click No and ignore the Rufus message (may or may not still work)
2. select to write in dd mode (this is what I usually do and have never had an issue)

---

### Post by gezzer2 on 2024-05-01
you could try if you have gnome disks installed .. right click the ISO image of Kubuntu and choose 'open with'
choose 'disk image writer'

follow the instructions from there to burn the ISO to make a bootable USB ..

---

### Post by ActionParsnip on 2024-05-01
Be sure the SHASUM the ISO before you use it (or use torrents) so you know the ISO is complete and consistent

---

### Post by Omnios on 2024-05-01
So apparently this error has nothing to do with the Kubuntu ISO but rather is an error pertaining to the Rufus program and should not affect the USB ISO.

---

### Post by TheFu on 2024-05-01
> **Omnios said:**
> So apparently this error has nothing to do with the Kubuntu ISO but rather is an error pertaining to the Rufus program and should not affect the USB ISO.

That is unknown, but it is not likely, as thousands of people have used the ISO successfully.  We are making suggested based on what is likely ... which comes back to local issues.  While it does happen, even more seldom would be issues with the hardware and the distro, but not much about that has been provided, so we are sticking to the most likely issues.

Rufus, corrupted download, perhaps an incompatible flash drive, firmware, or USB port.  Those tend to be the most common problems. That's why we started with those in most responses.

---

### Post by Omnios on 2024-05-03
So after playing around with Rufus learnt this error "[COLOR=#000000]error page with image uses Grub 2.12 but only includes files for Grub 2.06 error" [/COLOR] Is not about the Kubuntu ISO but was rather that Rufus wanted to use 2.12 and was a prompt to download 2.12 from Rufus download Page. Also looking into burning a Debian Live Disk and had another such error to download Rufus files to burn the Debian ISO. Apparently Rufus does not have all the burner files in the downloaded program and will prompt to download needed files.  This error accurse before actually burning the ISO image.

---

