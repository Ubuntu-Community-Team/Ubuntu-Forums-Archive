---
title: "Standby/suspend Karmic 9.10 issues..."
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GSF1200S on 2009-08-29
Hello people! Im in need of some guidance on sleep/suspend as the title of this thread suggests. 

I have an Asus Eeepc 1005HA-P currently running 9.10 devel UNR. While suspend and resume work perfectly, never hanging or failing to do as expected, my wireless has issues. It will reconnect, but it is unstable and will often stall or disconnect.

Since Im using the ath9k module, im pretty sure it doesnt directly support suspend/resume. I have found that rmmod ath9k before and modprobe ath9k after resuming solves the isse. 

So, my question: Does anyone know for sure what scripts are initially called (scripts with root priveledge) when the lid is closed, the sleep button is pushed, and the script called upon resume? I have found what appears to be the sleep script in /etc/acpi/sleep.sh, but im not sure.

Any ideas?

---

