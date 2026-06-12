---
title: "Minimize, maximize and close buttons disappeared after kernel upgrade to 2.6.32-22"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by duduklein on 2010-06-05
I have installed all the updates recommended by the update manger and one of them was the kernel upgrade from 2.6.32-21 to 2.6.32.22.  

When I log in to the new kernel (2.6.32-22), my layout buttons (minimize, maximize and close) don't appear anywhere. My first attempt to solve the problem was going to gconf-editor->apps->metacity->general and checking out the layout buttons. the string value was ":minimize,maximize,close", as I had disabled the menu button and had marked it as default and mandatory. When I tried to edit it, I was unable (this is probably normal, but I'm not a linux expert). Then I clicked on unset key and it became "menu::minimize,maximize,close".

In both cases (with and without the menu button on the left), the values were there, but the buttons were not. Very strange. Besides, when I tried to remove the "menu" button, I got the following message: "Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/metacity/general/button_layout' set in a read-only source at the front of your configuration path"

One other thing I noticed, that is not working, is that usually clicking on the top bar (where the layout buttons appear), it maximizes or restores the old size of the window and this is not working either. 

I assume this is a kernel problem, since when I log in using the old kernel 2.6.32.21, everything works fine. Obviously, there may be some other reason. 

EDIT: I found in another thread that executing the following command would solve the problem: "sudo aptitude purge ubuntu-desktop && sudo aptitude clean && sudo aptitude update && sudo aptitude install ubuntu-desktop && sudo /etc/init.d/gdm restart". Actually, after restarting the computer, everything was normal again, but then I turned it off and when I started it again, the problem above had reappeared, so this solution does not work.

Any ideas on how to solve this?
Thanks

---

