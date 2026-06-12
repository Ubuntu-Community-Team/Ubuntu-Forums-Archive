---
title: "[SOLVED] What kernel version"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2008-10-10
What version of the kernel does the current 8.10 release use?

---

### Post by wgrant on 2008-10-10
> **Jordanwb said:**
> What version of the kernel does the current 8.10 release use?

2.6.27 final was uploaded yesterday.

---

### Post by Jordanwb on 2008-10-10
That's the one that 8.10 uses?

---

### Post by wgrant on 2008-10-10
> **Jordanwb said:**
> That's the one that 8.10 uses?

8.10 is the development release at the moment, so yes.

---

### Post by Jordanwb on 2008-10-10
All right thanks. So it would be safe to assume that any wifi cards that can be supported in linux (without ndiswrapper) would work in the LiveCD

---

### Post by igknighted on 2008-10-10
> **Jordanwb said:**
> All right thanks. So it would be safe to assume that any wifi cards that can be supported in linux (without ndiswrapper) would work in the LiveCD

Not really... often they need to download some firmware that cannot be distributed on the CD (broadcom, for example, and I believe Atheros and Intel as well.  I know Fedora and Suse require you to get that firmware elsewhere, as some of it is non-free).  I don't think the program that grabs these non-free pieces runs on the liveCD, so you can run it manually (if online) or install and it will run on first boot.

---

### Post by Jordanwb on 2008-10-10
All right thanks.

---

