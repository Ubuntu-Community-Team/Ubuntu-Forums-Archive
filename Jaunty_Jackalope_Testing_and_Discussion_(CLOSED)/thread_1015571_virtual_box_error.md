---
title: "virtual box error"
date: 2008-12-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by computerfreak on 2008-12-18
i just finished installing jaunty in virtualbox and when it rebooted to load from the hdd it said my kernel need pae from the cpu but its not present. check out the screenshot in the attachments. how do i fix this, or should i wait the hour for alpha 2?

EDIT: sorry forgot today was the 18, should i still try alpha 2?

---

### Post by cszikszoy on 2008-12-19
Go to the settings for your VM, go to the general section, then advanced tab.  Uncheck the box that says "Enable PAE/NX".

---

