---
title: "How do you run the 'checksum' test?"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-06-21
Just burned the iso image for 32 and 64 bit 12.04 and don't see and can't recall how to run the checksum test to check for errors.

How do you run this test for 12.04 images?

---

### Post by codemaniac on 2012-06-21
Hello cybrsaylr ,

The below link will refresh your memory . :)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cybrsaylr on 2012-06-21
Thanks for the link codemaniac but I vaguely recall there was an easier way to run that check.

---

### Post by black veils on 2012-06-21
within ubuntu i use GtkHash. for Windows  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)    scroll down to the header **MD5SUM on Windows**.



[]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by cybrsaylr on 2012-06-21
Yep!
This is the way I used to check in the past.
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

Is that still available for 12.04?

---

### Post by black veils on 2012-06-21
it would be a lot easier to use GtkHash app from software centre, but if you want to do a disc check (which i doubt is the same as an ISO check) then there should be an option.

---

### Post by cybrsaylr on 2012-06-21
OK, I just tested 3 iso images I burned with:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
and they all tested OK and error free.
Used CDIntegrityCheck because I was familiar with it and it didn't really take that long. Just forgot how to get to that CDIntegrityCheck test page.

The first iso image was burned with Brasero at 18-24X times speed because I couldn't get Brasero to burn any slower.

Used K3B to burn the next two iso images at 4X times speed. 

That said all 3 tested error free but have read it's best not to burn an iso image at a fast burn speed.

---

### Post by black veils on 2012-06-21
you are meant to check the ISO before you burn. and yes it needs to be burned at the slowest speed like 1x 2x 3x

with GtkHash you put the MD5SUM from ubuntu website into the "check" area, then load the ISO file into the app, press **Hash** and it will check for you, with a confirmation icon!

---

### Post by cybrsaylr on 2012-06-21
Thanks black veils.
Will give that a try also.

---

### Post by cybrsaylr on 2012-06-21
Figured GtkHash out, gave it a try and got this.
But it didn't show the  "check" area, or confirmation icon you meentioned.

[IMG]http://farm8.staticflickr.com/7110/7416069062_7186c089c4.jpg[/IMG]

[IMG]http://farm9.staticflickr.com/8148/7416069046_4e42ff6949.jpg[/IMG]

---

### Post by black veils on 2012-06-21
weird, that is the older version, what you do then is manually check the MD5SUM against the one on ubuntu website [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Edit:

an easier way would be to try the app mentioned on here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

scroll down to  [SIZE=2]**MD5SUM with "Checksums calculator"**, says it works on windows and linux[B].
[/B][/SIZE]

---

### Post by cybrsaylr on 2012-06-21
> **black veils said:**
> weird, that is the older version, 

This is the version I got from Synaptic package manager:GtkHash 0.3.0 and posted it because I was totally unfamiliar with it, then did a  manual check of the MD5SUM against the one on ubuntu website.

---

