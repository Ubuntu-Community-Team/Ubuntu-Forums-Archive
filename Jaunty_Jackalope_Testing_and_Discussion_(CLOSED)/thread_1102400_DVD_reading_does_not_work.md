---
title: "DVD reading does not work"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Asraniel on 2009-03-21
Hi there,
i try to read a DVD under jaunty, but it does not really work. I tried installing all the codecs, restricted-extras and of course that shell script you can execute to install libdvdcss. Any idea why it does not work? i never had this problem with other versions of ubuntu, has something changed that i need to know?

thank you very much and congratulations for that great release

---

### Post by exploder on 2009-03-21
I am able to get a DVD to play but I have to move the slider to get going. I filed a bug report but have not received the e-mail for it yet. This is not a final release, it is still in beta so this type of thing is not unusual. 

I used the guide in the Multimedia & Video section to compare what I installed to make certain I did not miss anything. You might want to have a look there too.

---

### Post by rburkartjo on 2009-03-21
yea i can only get them to play with xbmc and smplayer (i had to update to get to work) vlc and movie player wont work

---

### Post by Nullack on 2009-03-21
gstreamer uses resindvd for dvd navigation - its buggy and feature incomplete.

IMHO the best way to go is to use an svn compile of mplayer with the smplayer front end. Though, this isnt 100% either for dvd navigation but no free linux dvd solution is 100%.

---

### Post by zekopeko on 2009-03-21
> **Asraniel said:**
> Hi there,
i try to read a DVD under jaunty, but it does not really work. I tried installing all the codecs, restricted-extras and of course that shell script you can execute to install libdvdcss. Any idea why it does not work? i never had this problem with other versions of ubuntu, has something changed that i need to know?

thank you very much and congratulations for that great release

do you have the medibuntu repo?

---

### Post by Nullack on 2009-03-21
Why does he need it? He already said that he grabbed the css decryption library using the supplied script.

---

