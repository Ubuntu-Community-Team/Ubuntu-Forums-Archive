---
title: "Unable to boot after upgrading from 23.4 to 23.10"
date: 2024-04-29
forum: Installation &amp; Upgrades
---

### Post by rsh23 on 2024-04-29
[IMG]https://imgur.com/a/BGLBhQn[/IMG]Hi,
I upgraded from ubuntu 23.4 to 23.10 on an old Lenovo laptop and it is freezed on boot menu and when I choose any of the options then it start rebooting and after 5min it is back again on the same boot menu.
Would be great if you could help me here.

[https://imgur.com/a/BGLBhQn](https://imgur.com/a/BGLBhQn)

Kind Regards,
Rsh[IMG]https://photos.google.com/photo/AF1QipNaYH6ieh5IEdyFDgFhYDCG6Wbx0ca6QRVhhw4H[/IMG][IMG]https://photos.google.com/photo/AF1QipOhGU7MKnxnG8YrvGterry8xkX8pYrSkOWKzVeR[/IMG][IMG]https://photos.google.com/album/AF1QipMkDUYcZSGq-wfJ2eraK1lt46sVcpYuyBRxP9MD[/IMG]

---

### Post by Impavidus on 2024-04-29
That looks like an uefi menu.

Is there anything legible on screen between choosing Ubuntu and returning to the menu? You could try [boot repair]("https://help.ubuntu.com/community/Boot-Repair") and create a summary. That may give a lead. Have you got backups of your documents?

Anyway, troubleshooting a release upgrade gone wrong is hard and often not worth the effort. A fresh install will be easier. Your 23.04 system was already 3 months past end-of-live, 23.10 only has 3 months left and 24.04 LTS has already beeen released, so a fresh install of 24.04 LTS may be the easiest way out of your problem.

---

### Post by rsh23 on 2024-04-30
Many thanks for your reply. Unfortunately, I have no backups! There is no other options than what I see on the screen. 
How can I do boot repair. I tried to go to recovery mode but wasn't successful with that too.

Kind Regards,
Rsh

---

### Post by Rubi1200 on 2024-04-30
You need to boot the laptop with a live USB and choose to Try Ubuntu.

Then follow the instructions to run the boot info script (same as boot repair). Do not try and repair until we can see what is going on. Choose to do a summary report and pick the option for a pastebin link. You can then post that link back here.

---

### Post by Impavidus on 2024-05-01
Using the same live usb you can also access your filesystem and create backups on an external drive.

---

