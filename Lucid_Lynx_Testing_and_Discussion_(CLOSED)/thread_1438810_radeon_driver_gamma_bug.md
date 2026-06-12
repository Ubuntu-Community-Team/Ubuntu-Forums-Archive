---
title: "radeon driver gamma bug?"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xzero1 on 2010-03-25
Using the (default) radeon driver is there a way to adjust the display gamma/brightness or do I have to consider this a bug?

---

### Post by Rob2687 on 2010-03-25
xgamma?

---

### Post by xzero1 on 2010-03-25
Thanks.

---

### Post by xzero1 on 2010-03-25
While xgamma does affect the display, I am still convinced there is an issue with the gamma/brightness/contrast with the current driver. If I set the gamma to the same value that I get with Karmic and test using some web pages designed for monitor calibration, then the display gets even worse. The default xgamma setting 1.0 makes the text input boxes virtually disappear whether in the browser or not using the standard preset values on my display. As minor an issue as it may sound, it really affects the readability and appearance of various websites including this one.

I am using the default radeon driver on a hd 4770 (r700) on a desktop machine. Before filing a bug report, does anyone else have issues like this or have a fix?

---

### Post by raido357 on 2010-03-26
I have the same problem with Radeon X800.

It works fine with previous kernel 2.6.31-20.

xgamma makes it worse.

Edit: I reported it: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/548709](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/548709)

---

### Post by xzero1 on 2010-03-26
I have added camera photos to illustrate the issue. The camera is set to identical manual settings for each screen shot and take a picture of a single file in Lucid and Karmic. I have added the original photos to the bug report filed above. Notice in particular the init and collector rows and the lack of detail and shading in the Lucid shots. For anyone using the radeon driver, please check this issue and subscribe to the bug report if applicable.

Photo explanation:

2149: Lucid at default xgamma settings
2150: Lucid at xgamma .6
2151: Karmic at default settings
2152: Karmic at xgamma .6

---

