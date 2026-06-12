---
title: "Intrepid upgrade to Jaunty"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Gramps on 2009-04-01
I remember reading this and now I can't find it. I want to upgrade my Intrepid machine to Jaunty.

I believe what needs to be done is to go to sources and change Intrepid to Jaunty then
sudo apt-get update
sudo apt-get dis-upgrade

Then we can do some testing in the final stages of development.

---

### Post by Rallg on 2009-04-01
Here is what worked for me:

In Terminal,

update-manager -d

(I do not recall if sudo was needed.)

When the update manager window appears, you will see a "new distro is available" choice. Click it and follow instructions.

The download are very large. If you cannot complete all the downloads at once, it is possible to close the Terminal (it will warn you), then resume later, (again using update-manager -d). But don't do that after downloads have completed.

---

### Post by taavikko on 2009-04-01
> **Gramps said:**
> upgrade my Intrepid machine to Jaunty.

I believe what needs to be done is to go to sources and change Intrepid to Jaunty then
sudo apt-get update
sudo apt-get dis-upgrade



This method isn't supported or proposed.

Either use "update-manager -d" or "sudo do-release-upgrade -d"
Check that "normal" is set to release upgrades
Either in software-sources, or in "/etc/update-manager/release-upgrades"

---

