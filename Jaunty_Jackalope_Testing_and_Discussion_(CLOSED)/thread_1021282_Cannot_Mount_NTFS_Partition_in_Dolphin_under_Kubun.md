---
title: "Cannot Mount NTFS Partition in Dolphin under Kubuntu"
date: 2008-12-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jonnybecker on 2008-12-25
Hi,

I have just installed Kubuntu Jaunty (Alpha 2) on my mums computer yesterday. Now I have the problem, that I cannot mount NTFS-partitions in Dolphin. The partitions are listed, but when I try to access them I get the following message.
> An error occured while accessing 'Volume (ntfs)', the system responded: org.freedesktop.Hal.Device.Volume.InvalidMountOption: The option 'loclae=en_US.UFF-8' is not allowed for uid=1000
With Intrepid I didn't have this problem.

Does anyone else have this problem or know how to fix it?

Cheers
Jonny

---

### Post by Gina on 2008-12-25
You should only install a development system like Jaunty on a test machine - there will be many problems.  There is even a possibility, albeit remote, of it destroying data on other partitions.  I think there is a known problem currently with NTFS partitions and Jaunty.

---

### Post by jonnybecker on 2008-12-25
Hi,

> You should only install a development system like Jaunty on a test machine
This is my test machine. Jaunty is installed alongside with Win XP.

> I think there is a known problem currently with NTFS partitions and Jaunty.
Good to know.

Cheers
Jonny

---

### Post by ShirishAg75 on 2008-12-31
Has anybody filed a bug for the same?

---

### Post by Vorian on 2009-01-01
it's more of a feature request, but there is a solution in the works.

Sit tight :)

---

### Post by Gina on 2009-01-01
I checked this out myself on my laptop, which is still running Jaunty quite happily and also found I couldn't mount NTFS partitions which confirms that it applies to straight Ubuntu as well.

---

### Post by plun on 2009-01-01
> **Gina said:**
> I checked this out myself on my laptop, which is still running Jaunty quite happily and also found I couldn't mount NTFS partitions which confirms that it applies to straight Ubuntu as well.

For Gnome its just that ntfs-config is missing for unknown reason.

Install and run the GUI and it should work again.

Package info:
[http://packages.ubuntu.com/jaunty/ntfs-config](http://packages.ubuntu.com/jaunty/ntfs-config)

(too tired to look for the bug-report for this)

---

### Post by Gina on 2009-01-01
Thank you very much - that's fixed it :):)  I now have access to my NTFS partitions.

---

