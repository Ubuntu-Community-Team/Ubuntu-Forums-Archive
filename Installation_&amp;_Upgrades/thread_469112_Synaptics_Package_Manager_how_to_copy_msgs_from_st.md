---
title: "Synaptics Package Manager how to copy msgs from status Terminal window?"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by mcook2 on 2007-06-09
Using Synaptics Package Manager (SPM) on Feisty ....

I keep a "System diary" and I like to copy error messages there so I can annotate them as I work on solutions --  helps me to remember what I was doing/did on a particular day,  how I worked around problems, etc.

However, with the default preferences set in SPM I could not (still cannot) see how to copy messages from the pop-up Terminal window that appears when you are doing an Apply and shows you the progress.  I have tried highlighting the text and doing a Ctrl+C but this doesn't work.  Is there another keystroke combination one has to use to do this? Is there room for an enhancement here?

See also following post re. lost History entry for SPM ... a separate issue.

---

### Post by bapoumba on 2007-06-11
Not using synaptic.

History should be in **/root/.synaptic/log**.
Just had a look, you need to be root to list the files there (I guess as synaptic is always run with root privileges).

---

### Post by mcook2 on 2007-06-13
Hey Bapoumba,

Yes, I can see the History entries in /root/.synaptic/log, and indeed these do contain exactly the same information as what you see when you using File > History in SPM itself.

What I'm looking for is the next level of detail. When you are installing something and you click on Details in the "Applying Changes" pop-up that appears you can see a little Terminal window that lists the progress in more detail, including any error messages, like this:

[IMG]http://skyprod.net/~mcook/images/Ubu-Scrnsht-SPM-Changes-applied.png[/IMG]

You can also get a bigger version of this same terminal window by clicking Apply changes in a terminal window in SPM >  Settings / Preferences > General tab. 

What I want to be able to do is to copy text out of that terminal window so I can save it to look at later.  Otherwise when you close the window after the install completes you have lost the information.

How can I do that?  Is there a special keystroke combination to use, as Ctrl+C doesn't work?

Alternatively, do these additional install messages get logged anywhere?

---

### Post by bapoumba on 2007-06-13
This is a regular terminal window, the messages are the same you get when using apt-get. Did you try highlight+Shift-CTRL-C to copy (and CTRL-V or middle click to paste in a text editor)?

In the terminal, CTRL-C has a special meaning (stop current action), so copy is Shift-CTRL-C and paste (in a terminal) is Shift-CTRL-V (or middle click).

CTRL-C and CTRL-V anywhere else.

---

### Post by mcook2 on 2007-06-14
Hey - thanks again, 

Ya, I had this synchronistic flash of inspiration while working on s.t. else to do with X -  that it needed some  weird keystroke combination that I forgot several tech lives ago - I'll try it when I get back from work.

Feeeling noobish, 

Yrs truly,

M.C.

---

### Post by bapoumba on 2007-06-14
> **mcook2 said:**
> Hey - thanks again, 

Ya, I had this synchronistic flash of inspiration while working on s.t. else to do with X -  that it needed some  weird keystroke combination that I forgot several tech lives ago - I'll try it when I get back from work.

Feeeling noobish, 

Yrs truly,

M.C.
You're welcome. Ah, those flashes that strike you when doing completely unrelated things! I know that.
(and we always have something to learn, so newbie here forever \o/).

---

### Post by mcook2 on 2007-06-15
Thankyou - it works a treat - "Ever Onward!", as we used to sing.

---

### Post by bapoumba on 2007-06-15
> **mcook2 said:**
> Thankyou - it works a treat - "Ever Onward!", as we used to sing.
He he :)
And you're welcome.

---

