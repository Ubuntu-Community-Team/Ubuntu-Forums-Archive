---
title: "Two software updaters after upgrading to Ubuntu 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2013-10-20
[SIZE=4][FONT=comic sans ms]On the[/FONT][/SIZE] sevententh I upgraded to Ubuntu 13.10 from 13.04. I used the regular upgrade routine and all seemed to be going smoothly. Then early yesterday I beleive there was a problem with upgrading the browser Google Chrome, which was one of my Internet browsers. Here I am afraid to say my memory may be suspect. It is quite possible I interrupted the upgrade some how. In any case I unistalled Google Chrome stable then ran an update through the terminal. 
I spent the next several hours doign my thing. Then late in the afternoon I opened Dash to check the Software Updatee as is my routine and wa surprised to see not one but two Software Updater icons. 
I clicked both the first one ran normally in  that small windiow giving me a no updates avalable indication. The second one however came up with this:

/home/bill48/Pictures/Screenshot from 2013-10-20 08:37:32.png

Then the next shot was this:

/home/bill48/Pictures/Screenshot from 2013-10-20 08:38:12.png

I do not know what it could mean other then the upgrade being refered to is or was the upgrade for the Browser "Google Chrome"? Here is another thing in the Ubuntu Software Center it shows an 'Software Updater' but it does not have the green checkmark indicating it is installed. When I clicked on it, it showed the install button. 
I am now confused and am wondering what does it all mean my having in Dash two "Software Updater's" and yet in the 'Ubuntu Software Center' it shows a 'Software Updater" that apparently has not been installed. Now here I may need to make a retraction in my statement about finding the Software Updater not showin it as being installed. I just did a quick check of the U. S. C. and found that little green check in the lower right corner showing it is installed. 
I went back an opened Dash and noticed this:

/home/bill48/Pictures/Screenshot from 2013-10-20 08:59:59.png

Which shows the two updater's but the second one, which I did not notice at first says 'Software Update' an not 'Software Updater'  
Now comes the big question that being should I take notice of the warning the "Softward Update" shows or ???

bill23

---

### Post by bill23 on 2013-10-20
Sorry the screenshots did not show up.

---

### Post by bapoumba on 2013-10-20
> **bill23 said:**
> Sorry the screenshots did not show up.

Sometimes, the forums file uploader is, well, difficult to work with. In the "Manage Attachments" item, you may have to upload the files several times before they get actually picked up, even when they are of regular file format and size.

---

### Post by bill23 on 2013-10-20
bapoumba;

You are probalbly right but my luck with posting screenshots is not too good. In any point of misdirection here is what the shots would have read. 

The first was of the 'Software Updater' showing ther was no software to be updated. 
The second screenshot was of the 'Software Update' and it had two windows;  the 'software updater' window overlapping the warning.

Here is what the warning was: 

"Could not get list of Distribution Upgrades.
 Failed to process requests. (there was a more)
The backend exited unexpectedly. This is a serious error as the spawned backen did not complete the pending transaction."

I opened 'Software & Updates and in the 'other software' were a number that said 'disabled on upgrade to saucy./ i left them alone. I unchecked one relating to Google Chrome stable.

Here is a kicker, I went to the Software Center, typed in 'Software Update' and up popped and icon appearing like the software update(r). Under it read: update software installed on the system. I clicked it and this is what showed up:

NOT FOUND
There isn't a software package called 'gnome-update-viewer in your current software sources.'

I also checked out Synapatic Package Manager and it had nothing. I have a Gnome desktop environment that I use occasionally. I have checked there and I get the 'software updater' and also the 'software update' too. I've hear fo a commandline for removing Apps or other items through the terminal but have not tried for two reasons; I am sure of the command and if I went ahead I could make matters worse. Which I don't want to do.

I think the comman would be something like this:  'sudo apt-get rmove software update'   Does that look right? I have had warnings before that came to be nothing in the end. What about this one?

bill23

---

### Post by bapoumba on 2013-10-21
Well, first please paste the outputs to:
```
sudo apt-get update
sudo apt-get upgrade
```

If the upgrade got interrupted, maybe we can get it to complete, depending on these results.

---

### Post by bill23 on 2013-10-21
I did use both commands and at the time there was no updates and no upgrades. I resolved my problem by one; saving files and folder onto a usb flash drive, two; reinstalled my former Ubuntu 13.04 and three; installed Ubuntu 13.10 on my PC. This was through the Software Updater, I had tried to use the command 'sudo apt-get distro upgrade' but it did not show a upgrade so I took my other option.

It was a drastic move an perhaps another method could have been used to resolve things, but that is a 'might have' and I saw one sure way and I took it.

Thanks for the help you tried to give me,

bill23

---

### Post by bapoumba on 2013-10-22
Glad to see you fixed it. Solved and working is solved and working :)

---

