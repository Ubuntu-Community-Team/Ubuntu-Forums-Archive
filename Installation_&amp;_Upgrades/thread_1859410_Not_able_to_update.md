---
title: "Not able to update?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by cbennett a7xftw on 2011-10-13
Well, I am trying to update from 11.04 to 11.10 but i get this error:

W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What do i do??

---

### Post by jermaine151 on 2011-10-13
> **cbennett a7xftw said:**
> Well, I am trying to update from 11.04 to 11.10 but i get this error:

W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What do i do??

I have the exact same issue. I keep going into my software sources and removing the cdrom entry and I also unchecked the Ubuntu cd under Ubuntu Software tab and it's still happening.

---

### Post by Old_Grey_Wolf on 2011-10-13
Open update manager and click on the settings button. In the Software Sources window, go to the "Ubuntu Software" tab. Near the bottom, untick the CDROM box. Close that window, click on "check" and you should be OK.

---

### Post by jermaine151 on 2011-10-13
> **Old_Gray_Wolf said:**
> Open update manager and click on the settings button. In the Software Sources window, go to the "Ubuntu Software" tab. Near the bottom, untick the CDROM box. Close that window, click on "check" and you should be OK.

I tried that first :( and it failed and then I went to "Other Software" tab and saw 2 [cdrom:" entries in there, removed them and I still get the same issue.

EDIT: I should add that I'm trying to upgrade using the Alternate ISO mounted as a loop device to /media/cdrom.

EDIT 2: I never hit the check button after doing it, until I actually read your instructions better. It seems to be upgrading now. Thank you very much!

---

### Post by cbennett a7xftw on 2011-10-13
> **jermaine151 said:**
> I tried that first :( and it failed and then I went to "Other Software" tab and saw 2 [cdrom:" entries in there, removed them and I still get the same issue.

EDIT: I should add that I'm trying to upgrade using the Alternate ISO mounted as a loop device to /media/cdrom.

EDIT 2: I never hit the check button after doing it, until I actually read your instructions better. It seems to be upgrading now. Thank you very much! LOL same thing

---

