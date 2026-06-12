---
title: "Will not start x srever"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by darthmill on 2007-06-13
I have installed Ubuntu desktop and all went well untill it restarted.
I get a message Failed to start the X server.
I need to know how to configure x server in terminal mode.:(

---

### Post by 67GTA on 2007-06-13
When grub loads, choose the recovery mode. This will drop you into a terminal window. Run the command "sudo dpkg-reconfigure xserver-xorg" without the quotations. This will take you through the steps to get Xserver going. You need to know which graphics driver you are using  and info about your monitor(horz.-vert. refresh rates,resolution). If you are not sure of an answer, just hit enter.

---

### Post by darthmill on 2007-06-13
thanks your a life saver

---

