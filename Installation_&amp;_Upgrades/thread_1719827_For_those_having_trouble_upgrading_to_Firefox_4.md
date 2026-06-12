---
title: "For those having trouble upgrading to Firefox 4"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by aosgd on 2011-04-02
I have found a solution!

WARNING: SAVE YOUR BOOKMARKS/PASSWORDS/ANY OTHER PERSONAL INFORMATION!! THIS WILL ERASE EVERYTHING TO DO WITH FIREFOX!


Step 1:

In terminal run the commands:

```

sudo apt-get remove firefox*
sudo apt-get remove mozilla*

```Step 2:

Remove Firefox icons from Application -> Internet -> Mozilla Firefox (This should already be done, though.)

Also remove any shortcuts you may have on your desktop or panel. 

Step 3:

Download the latest version of Firefox from here:  

[http://www.mozilla.com/en-US/products/download.html?product=firefox-4.0&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-4.0&os=linux&lang=en-US)

Step 4:

In terminal go to where you downloaded Firefox (default is /home/username/Downloads)

```

cd /home/username/Downloads

```Now execute this command to extract the contents

```

tar xjf firefox-*.tar.bz2

```Next, you will move the contents of the extracted folder to your home folder.

```

mv /home/username/firefox /home/username

```(For beginners, this runs the move command to move firefox from the first location to the new location.)

Step 5:

Right click on your desktop, select "Create Launcher..."

Type: Application
Name: Firefox (or Mozilla Firefox -- it's up to you)
Command: /home/username/firefox/firefox
Comment:  Runs Mozilla Firefox 4.0

Click OK.

You should now be able to double-click on this and run Firefox 4.0!

--------------------------------------------------------------------------------------------

1. If you want to modify the shortcut to use the firefox icon, right click on the file you created titled "Firefox" on your desktop, go to Properties. 

2. You will see at the top left what looks like a screw, click on it (the picture) and go to your home folder, click on the firefox folder, and then click on the icons folder.

3.  You should see a file named "mozicon128.png"  click on this and click Open.

4. Close the next window, and your icon should be updated!

5. Enjoy!

---------------------------------------------------------------------------------------------

If there are any questions/comments/concerns please leave them here and I will get back to you.  I am just starting out with Linux, so I might not be able to answer everything.

---

### Post by jcolyn on 2011-04-02
A lot of extra work with this method.

The below will upgrade Firefox 3.6.x to Firefox 4 stable not the nightly builds....

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
``` ```
sudo apt-get update
``` ```
sudo apt-get install firefox ubufox
```

---

### Post by aosgd on 2011-04-02
I tried that exact same thing, minus the "ubufox" while running the apt-get install command.  Even after upgrading through terminal/packet manager version 3.6 was still running.

Since I have it running good on my PC, I might toss it up on a virtual machine on my Win7 PC and test that out.  If it works, excellent, if not, my method will.

---

