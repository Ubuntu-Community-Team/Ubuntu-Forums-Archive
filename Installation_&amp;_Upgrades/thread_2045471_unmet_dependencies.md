---
title: "unmet dependencies"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2012-08-21
The following packages have unmet dependencies:
 libasound2-dev : Depends: libasound2 (= 1.0.25-1ubuntu10)
 libqt4-dev : Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-designer (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-help (= 4:4.8.1-0ubuntu4) but it is not going to be installed
              Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-qt3support (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-scripttools (= 4:4.8.1-0ubuntu4) but it is not going to be installed
              Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-svg (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-test (= 4:4.8.1-0ubuntu4) but it is not going to be installed
              Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
              Depends: qt4-linguist-tools (= 4:4.8.1-0ubuntu4) but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4:4.8.1-0ubuntu4) but it is not going to be installed
              Recommends: libqtwebkit-dev (>= 2.0~) but it is not going to be installed
 libsvn-dev : Depends: libaprutil1-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
michael@michael-ubuntu:/media/DATA/FGFSn$

sigh...what to do?
Thanks

---

### Post by MikeCyber on 2012-08-21
solved by manually selecting qt4 in the update manager. 

The update manager is kind of freaky. Selecting all would have broken my system! Xorg breaking Nvidia and kernel most likely the whole OS.
Freaky...yea Linux still is...

---

### Post by cortman on 2012-08-21
> **MikeCyber said:**
> solved by manually selecting qt4 in the update manager. 

The update manager is kind of freaky. Selecting all would have broken my system! Xorg breaking Nvidia and kernel most likely the whole OS.
Freaky...yea Linux still is...

How do you know that these updates would have "broken your system"?

---

### Post by Bucky Ball on 2012-08-21
> **MikeCyber said:**
> solved by manually selecting qt4 in the update manager. 

The update manager is kind of freaky. 

Not suprisingly. Now you've solved the problem you can see all the missing dependencies contained 'qt' so freaky becomes obvious. But freaky things sometimes do happen, yes! It's the ones that take two days to figure out I don't love. ;)

Please mark as 'Solved' from thread tools to help others.

---

### Post by MikeCyber on 2012-08-21
Yes my fault. I had another conflict tiff - jpeg62, hence I decided to risk a full update. Reinstalled Nvidia and all is fine. The only drawback seems that a full update installs all kind of stuff.
Some years this went wrong but apparently this has improved. ;)

---

### Post by jcoles on 2012-09-06
> **MikeCyber said:**
> solved by manually selecting qt4 in the update manager. 

The update manager is kind of freaky. Selecting all would have broken my system! Xorg breaking Nvidia and kernel most likely the whole OS.
Freaky...yea Linux still is...

I have a similar problem with apache. But I don't understand how I can select a specific application in the Update Manager. The only packages listed there are the ones with available updates. Can you explain what you mean?

---

### Post by Bucky Ball on 2012-09-07
> **jcoles said:**
> I have a similar problem with apache. But I don't understand how I can select a specific application in the Update Manager. The only packages listed there are the ones with available updates. Can you explain what you mean?

This thread has been inactive for two weeks and the OP's problem has been solved. I advise you start a new thread with a descriptive title and give as much info as possible about YOUR problem specifically. You will get more help that way. Thanks and good luck.  ;)

---

### Post by jcoles on 2012-09-07
> **Bucky Ball said:**
> This thread has been inactive for two weeks and the OP's problem has been solved. I advise you start a new thread with a descriptive title and give as much info as possible about YOUR problem specifically. You will get more help that way. Thanks and good luck.  ;)

Thanks for the advice. 
Perhaps I misunderstood the injunction to "Search before posting a thread." If the found threads don't have the answer I need, then a new thread is best?

---

### Post by BlinkinCat on 2012-09-07
> **jcoles said:**
> Thanks for the advice. 
Perhaps I misunderstood the injunction to "Search before posting a thread." If the found threads don't have the answer I need, then a new thread is best?

Yes - ;)

---

