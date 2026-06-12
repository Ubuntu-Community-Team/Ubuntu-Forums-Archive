---
title: "Update Manager list item height chops description"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2008-09-21
I've noticed several times while testing 8.10 that the Update Manager occasionally will make all list items that can be updated shorter in height than normal.

While updates can still be applied fine, it looks jumbled and messy. I don't currently have a screenshot, but I can upload one as soon as it happens again.

A simple solution that seems to work most of the time is just closing the Update Manager and reopening it.

Has anyone else seen this or know if it's been reported or mentioned previously?

---

### Post by kyleabaker on 2008-09-22
Here is a screenshot from tonight. It happens like 1 in 5 updates at least...if not more. Closing and reopening usually fixes it.

[IMG]http://img301.imageshack.us/img301/2848/screenshotupdatemanagerik1.png[/IMG]

---

### Post by Nullack on 2008-09-22
That screenshot would make a useful bug report or an addition to an existing bug :)

---

### Post by forumache on 2008-09-22
I get it too.

I think (not at home right now) that, if I remember correctly, I can trigger it in a simple way: once it displays updates (looking fine), just press "Check for updates" again. The resulting display will look like the picture.

kyleabaker, this is your change to report a bug. if you don't, I will ;)

please check first that the bug was not already reported for update-manager package.

thanks.

---

### Post by waspbr on 2008-09-22
I got the same bug

---

### Post by kyleabaker on 2008-09-22
@forumache
I'm going to file it shortly. I'll post a link to the bug report. Thanks all.

---

### Post by kyleabaker on 2008-09-22
I couldn't find the same bug mentioned so I went ahead and reported it:
Bug #273184
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/273184](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/273184)

Go there and comment if you know more about how to trigger the bug or anything like that.

Thanks everyone.

Here is one more screenshot that I also attached to the bug report:
[IMG]http://img143.imageshack.us/img143/4223/screenshotupdatemanagerbo6.png[/IMG]

---

