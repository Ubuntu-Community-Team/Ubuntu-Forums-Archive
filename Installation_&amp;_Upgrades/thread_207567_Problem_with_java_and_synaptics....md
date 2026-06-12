---
title: "Problem with java and synaptics..."
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by Karai on 2006-07-02
Hi people!
Last days I install java with help of synaptics and the multiverse repository. All seems to be ok, but now everty time I make an update with synaptics it post me this message:

This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

How can I solve that?
Thanks!

If I have made some mistakes, sorry, my english is not perfect!!

---

### Post by blackjack6.21.91 on 2006-07-02
No worries, dude.

Try fixing broken packages in synaptic (if there are any).  In the left panel go to custom and then click broken.  Mark any packages in there for reinstallation.  Next go to "marked changes" and see if there's anything in there about java.  If there is, right click and do "unmark".

Next follow [this]("http://ubuntuforums.org/showthread.php?t=76702&highlight=install+sun+java") tutorial to install java via sun's website.

Good luck,
blackjack

---

### Post by Karai on 2006-07-02
I have tried your solution, but the message still appear.
Always the same message. I try to press return but it shows the same message all the time. After I have tried some times i write no and the installation continue and all seems to be Ok, but every time the message.
I want to remember that the problem is when I install any package of synaptics.
Thank you for your help!

---

