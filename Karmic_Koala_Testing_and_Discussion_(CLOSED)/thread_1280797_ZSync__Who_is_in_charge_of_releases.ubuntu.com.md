---
title: "ZSync / Who is in charge of releases.ubuntu.com?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by milaz on 2009-10-02
Dear people who are putting those tiny zsync files into releases folder!

First of all, I'd like to thank you for saving my bandwidth. ZSync is really a great idea, and it worked like a charm until karmic beta. Now I have a little request for you.

Please, rename "karmic-desktop-i386.iso" inside of zsync files to "ubuntu-9.10-beta-desktop-i386.iso" as you did rename these files itself in releases.ubuntu.com/releases/9.10. To be more exact, make the following change:

-------------------------------------------------------------
6c6
< URL: karmic-desktop-i386.iso
---
> URL: ubuntu-9.10-beta-desktop-i386.iso
-------------------------------------------------------------

This way testers will finally manage to zsync with this command:

zsync [http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.zsync](http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.zsync) -i karmic-desktop-i386.iso

Lots of bandwidth and man-hours of people figuring out how to fix zsync files locally will be saved, and grateful world will never forget your good deeds! 

Thank you.

---

### Post by ViRMiN on 2009-10-02
I mentioned that last night but, not in as much detail as you have!  I ended up MD5SUM'ing what I'd zsync'd in the morning or the previous day, and it was a perfect match so I left it at that.

---

### Post by vishalrao on 2009-10-03
OMG are they readying delta debs for karmic?!?! See [http://ubuntuforums.org/showthread.php?t=1215217](http://ubuntuforums.org/showthread.php?t=1215217)

---

### Post by Gourgi on 2009-10-03
> **vishalrao said:**
> OMG are they readying delta debs for karmic?!?! See [http://ubuntuforums.org/showthread.php?t=1215217](http://ubuntuforums.org/showthread.php?t=1215217)

i think above posts are mentioning ubuntu iso images and not packages delta debs.

quoting from the blueprint :
> 2009-10-01 robbie.w: This past week liw had been playing with debdelta-upgrade, but various issues meant he had not been able to get it to work yet. We're now in karmic-bug-fixing mode, so have to defer for potentially lucid, unfortunately. The good news is that debdelta does work, and its author seems to want to integrate it with apt.

---

