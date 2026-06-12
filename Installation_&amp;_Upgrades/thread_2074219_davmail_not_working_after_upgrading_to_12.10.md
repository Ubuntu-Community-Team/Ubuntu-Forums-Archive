---
title: "davmail not working after upgrading to 12.10"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by agualdino on 2012-10-21
Hi,

I can't run davmail after upgrading to 12.10 and I don't know why.

On 12.04 I had to allow it to the systemtray through dconfig-editor but now that's simply not doing the trick at all.

Loosing access to email (exchange account managed by thunderbird) after upgrading is very frustrating. Not to mention that the webapps are also not working for me.

---

### Post by astaticskyline on 2012-10-21
> **agualdino said:**
> Hi,

I can't run davmail after upgrading to 12.10 and I don't know why.

On 12.04 I had to allow it to the systemtray through dconfig-editor but now that's simply not doing the trick at all.

Loosing access to email (exchange account managed by thunderbird) after upgrading is very frustrating. Not to mention that the webapps are also not working for me.

Having the same exact problem. Any ideas?

---

### Post by arsenic77 on 2012-10-22
You can do the following to solve the problem:

apt-get install libswt-cairo-gtk-3-jni


;)

---

### Post by broomie on 2012-10-22
Cool and thanks I have this too -what does the cairo fix do BTW?

---

### Post by agualdino on 2012-10-22
Hi,

Thanks a lot for the tip Arsenic77, it fixed the issue!
:)

> **arsenic77 said:**
> You can do the following to solve the problem:

apt-get install libswt-cairo-gtk-3-jni


;)

---

### Post by agualdino on 2012-10-22
unfortunately all my tags are gone (what a nightmare of an upgrade)

> **agualdino said:**
> Hi,

Thanks a lot for the tip Arsenic77, it fixed the issue!
:)

---

### Post by broomie on 2012-10-22
fixed it for me too!

---

### Post by eMKi on 2012-10-23
Hi!

Installing this package also worked for me.

Thank you!

---

### Post by nitroguy on 2012-10-23
Genius!

---

### Post by REDGUMAU on 2012-10-23
Perfect result - many thanks! :guitar:

---

### Post by joschum on 2012-10-26
Great, it also works for me! Thanks a lot!!!

---

