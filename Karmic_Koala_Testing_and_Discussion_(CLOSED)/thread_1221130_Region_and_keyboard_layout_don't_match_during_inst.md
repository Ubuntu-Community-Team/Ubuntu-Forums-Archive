---
title: "Region and keyboard layout don't match during install"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-23
I reported this bug in Jaunty and it still exists in Karmic, [Bug 355563]("https://bugs.launchpad.net/ubuntu/+bug/355563")

Sequence of events:
1- Dvorak keyboard layout is selected at Live CD boot
2- Proceed with install
3- Select London as region
4- Preselected keyboard is US Dvorak instead of UK Dvorak

Also, moving down the list from US to UK quickly (using the cursor keys), the right hand list does not update or show the correct layouts, and tends to stick on Ukraine even though the left side has UK high lighted.

---

### Post by phenest on 2009-07-23
This was reported by another ([bug 398519]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/398519")). It seems this needs to be raised as a question rather than a bug.

---

### Post by phenest on 2009-07-23
[Question 77903]("https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/77903")

---

### Post by phenest on 2009-08-10
This is indeed a bug. I have also made another discovery. If I select a keyboard map on the Live CD boot screen, the suggested keyboard layout does not match the region I chose. However, if I don't select a keyboard map, the suggested layout *does* match the region, albeit I have to change the layout to Dvorak. So there is something wrong there.

---

### Post by Bert Mariën on 2009-08-10
The problem started already in Jaunty.

I need the Belgium keyboard, and it is preselected during install, but if I use the preselected I end up with a wrong keyboard.

Just never use the preselected keyboard, and select it yourself, even though the preselected shows the right keyboard.

I hope you're still with me. :lolflag:

---

### Post by zekopeko on 2009-08-10
There was some talk about further refining the time zone selector with country borders. That way all the relevant info could be auto gathered by using available GPS devices or by GeoIP lookup.

---

### Post by phenest on 2009-08-11
> **Bert Mariën said:**
> The problem started already in Jaunty.

Yes, there are bug reports that go back to Jaunty.

> **Bert Mariën said:**
> I need the Belgium keyboard, and it is preselected during install, but if I use the preselected I end up with a wrong keyboard.

But we are only talking about the preselected keyboard during install here.

> **Bert Mariën said:**
> Just never use the preselected keyboard, and select it yourself, even though the preselected shows the right keyboard.

Not much point in having a 'suggestion' if you're going to just select your own.

> **zekopeko said:**
> There was some talk about further refining the time zone selector with country borders. That way all the relevant info could be auto gathered by using available GPS devices or by GeoIP lookup.

That's doesn't not appear to be the problem. For example, if I select a Dvorak layout at boot, and Europe/London region during install, it suggests USA Dvorak. Right layout, wrong region. If I don't select any layout at boot (assumes Qwerty), and select Europe/London as a region during install, it suggests UK. Which is correct, but then I have to select Dvorak manually. It seems that selecting a layout at boot seems to upset it somehow.

---

