---
title: "New notification system woes"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-03-02
The new notification system looks good. I have two main problems with it - one because of a bug and one because of a feature.

1. The bug: the notifications do not work for me at all after login. I must do a "killall notify-osd -15", and then it works fine. Before that, trying to send test notifications with notify-send shows nothing, and brings no error message. Any idea where I should look in order to find the problem?

2. The feature: new notifications deprecate the text when they think it is too long. This is just NASTY. I have a beautiful hand-made system of dictionary scripts based on xclip, which shows definition using notification windows. Previously the definitions were shown wholly, resizing the notification window when too long. The new system just cuts out everything longer than three of four words! What gives? Is there a way to configure this? If the size of notification rectangular is fixed, is there a way to decrease the notification font size (without doing so for the rest of the system) so more text can be displayed?

---

### Post by JohnJackson on 2009-03-02
Yeah, I agree with your second point. Though the word you're looking for is truncate, not deprecate. I would like either to increase the width of the box or to have the title text drop down a number of lines when it's too long.

---

### Post by Stetzen on 2009-03-02
It seems to be that the amount of text in the notification box is specified by the HIG (found it in the ubuntu wiki). So probably it will be so little text in the notification for the rest of the life of the system :(

---

### Post by Wise Ferret on 2009-03-02
> **JohnJackson said:**
> Yeah, I agree with your second point. Though the word you're looking for is truncate, not deprecate.

:-#
Now if my dictionary system would function as it did in intrepid, I would not be making such mistakes.

---

### Post by mpt on 2009-03-02
> **Stetzen said:**
> It seems to be that the amount of text in the notification box is specified by the HIG (found it in the ubuntu wiki). So probably it will be so little text in the notification for the rest of the life of the system :(

I don’t know what you mean by “the HIG” (the [Gnome HIGs]("http://library.gnome.org/devel/hig-book/stable/") say nothing at all about notification bubbles), but the Notify OSD design spec says that [the title should take up to three lines]("https://wiki.ubuntu.com/NotifyOSD#Title%20text") and [the body should take up to ten lines]("https://wiki.ubuntu.com/NotifyOSD#Overflow%20of%20long%20messages"). Currently [this is broken]("http://launchpad.net/bugs/331367"), but it will be fixed, so don’t panic.

---

