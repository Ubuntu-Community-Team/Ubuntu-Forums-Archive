---
title: "[SOLVED] Gone back to Feisty - MODEM problem!"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2008-02-08
I've just reinstalled Feisty after going 'round and 'round with Gutsy.:(

 While everything worked fine before I tried upgrading, now I can't access the internet (again).

I installed the sl-modem-daemon and Gnome-ppp. The setup seemed to go ok.  Gnome-ppp detected my modem and created the /dev/ttySL0 simlink.  The modem will dial out, but will not connect and I get a "no carrier" message in the log.](*,)

What I would like to know is:

1.  Do I need to run ungrab-winmodem?

2.  Is it some other problem?

3.  Does anyone else have any ideas?

4.  Can anybody help?

5.  While I think Ubuntu is a great system and have been using it for several years.  Is there anyone at Canonical I can contact about getting WINMODEM support added to Hardy and later Ubuntu versions?  I'm fed up with having to reinvent the wheel every time I want to upgrade and I'm sure there are a lot of others out there are as well.

---

### Post by Goldpin on 2008-02-12
Problem solved.  Checked the "Stupid Mode" box in the Gnome-ppp setup.

However, is it at all possible for Linux to support winmodems without a lot of hassle?

---

### Post by zvacet on 2008-02-12
You can look if some of [these](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=modem&titlesearch=Titles) links may give you the answer.

---

