---
title: "Moving Home directory to second hard drive difficulties"
date: 2020-12-17
forum: Installation &amp; Upgrades
---

### Post by grxgghxrpxr on 2020-12-17
Hello everyone

I'm having difficulties moving my Home directory to a secondary hard drive.
I have successfully moved all the data over, mounted the new partition, then deleted the old directory.
But, when I edit the /etc/fstab file, I reboot, then when I log in, I type my password, it logs into a black screen for a few seconds then goes back to the login screen.

I have entered the following at the bottom of the file:
UUID=934ee40a-405c-41b4-82a7-f380c3d87f10      /home         ext4  defaults      0       2
(I've pressed tab in between each one)
Then saved it & rebooted.

Is there something I'm doing wrong?

Thanks
Gregg

---

### Post by ActionParsnip on 2020-12-17
Did you set the ownership of the data to your user?

---

### Post by grxgghxrpxr on 2020-12-17
> **ActionParsnip said:**
> Did you set the ownership of the data to your user?
How do I do that?

---

### Post by TheFu on 2020-12-17
chown - having correct ownership for the HOME of each userID on the system i pretty important. It is a little late for a question about that since there are different owners required. It really needed to be handled while everything was copied over.

Don't know if tabs matter or not since systemd-mount took over the fstab.  Use spaces in the fstab.

---

### Post by Impavidus on 2020-12-17
I don't know what you did exactly, so difficult to say what went wrong. I can point you to this very good guide for moving the /home directory to a separate partition. Maybe you find something you missed: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Most guides telling you how to do this would move the files with rsync, with options set to preserve ownership, so that shouldn't be a problem. But it does appear that your home directory is not where it should be, or its permissions or owner are wrong.

Can you switch to the TTY (ctrl+alt+F1 or some other F-key, use ctrl+alt+some other F-key to get back, depending on version and flavour of OS) and login? Have a look around with ls -l to see what's wrong.

---

