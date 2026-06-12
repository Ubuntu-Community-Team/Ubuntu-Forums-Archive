---
title: "Multiseat stops working after upgrading from 18.04 to 20.04"
date: 2020-06-30
forum: Installation &amp; Upgrades
---

### Post by williyamyam on 2020-06-30
Hello, I recently upgraded to 20.04 using sudo do-release-upgrade -d and I ran into some issues with my setup. Previously with 18.04 I was able to work with a multiseat setup using loginctl attach seatx [insert devices here]. I have multiple video cards which I thought I could use to set up separate sessions, but it seems to have been broken. I think this might have to do with the video card settings, as I have a Radeon 6670 and Nvidia GTX 1050 Ti. If I try logging in multiple users, I can only see the session from one video card at a time and the other user is booted off.

---

### Post by williyamyam on 2020-07-01
I found a hacky workaround by switching to lightdm. Now everything works fine, except for the aesthetic of the logon screen.

---

