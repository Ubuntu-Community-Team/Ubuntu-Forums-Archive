---
title: "custom kernel problem"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by uljanow on 2009-04-10
hi,
my custom kernel which works with intrepid fails to boot at all. The error message is "error initializing control socket". It doesn't pass the initramfs sequence.

Is this a known problem and are there any workarounds ?

---

### Post by iponeverything on 2009-04-10
Did you start with the config in /boot?

---

### Post by uljanow on 2009-04-10
The kernel config was fine but it looks like the initramfs and udevd use sockets for IPC so I had to add the unix domain socket module (unix.ko) to the initramfs. It's working now.

---

### Post by iponeverything on 2009-04-10
that is a good bit of information for me to file away.

thanks.

---

