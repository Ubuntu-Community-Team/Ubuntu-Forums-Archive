---
title: "Installing 10.04 Beta 2"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by cjwescott on 2010-04-15
Hi,

Tried installing using update-manager -d and received notification that my root does not have adequate space.  Removed most of what I can and I am still short 560 mb or so.  Even risking the removal of some questionable items I just don't see freeing up this much space to make it happen.

Is there another way to install 10.04?
Is there a way to increase the space allocation to root?

Stupid question but, can I delete the image file for 2.6.31-20 without affecting the 2.6.31-20 version?  Even if I can still not large enough to get to the 560 mb.

Chris

---

### Post by uRock on 2010-04-15
Are you using wubi or a full install? It looks like either way, you are going to need to back up data if you do not have a /home and do a clean install of 10.04.

---

### Post by cjwescott on 2010-04-15
I run Ubuntu as a full install.  I was hoping to perform the upgrade of 10.04.

If I download the iso file is there an option to upgrade when running it from the CD?

---

### Post by uRock on 2010-04-15
You can do that by downloading and burning the alternate installer image and then when it kicks the disk out, out it back in and it will offer the upgrade manager.

You may still have a problem with space though.

How many kernels are listed in your grub menu? If there is more than one, deleting each one will free up about 120MB. To delete kernels, go to Synaptic Package Manager and search 2.6.31 to display all of the Karmic kernels and uninstall every kernel accept the one you are using. There should be 3 listings for each kernel. DO NOT DELETE the one you are using. I added a screenshot of my Synaptic with the Lucid kernels showing. Once a new one is released, and I make sure that it works, I delete the others.

The next thing to try in order to clear space is to run computer janitor from the System> Administration menu.

Last but not least you can boot into recovery mode and there is an option there for cleaning up space.

If you end up doing a clean install, I would recommend making the / partition a little bigger.

Cheers,
Ronnie.

---

### Post by cjwescott on 2010-04-15
I did what I could in uninstalling programs and that is where I got down to needing another 560 mb.  With regards to removing other kernels I removed them all.  Of the latest kernel that I am still using I did not delete the image file.  This is 120mb or so.  Even if I could delete this it would not be enough.

Clean install is starting to make the most sense so that I can increase the Root.  Plus it would be nice to start fresh anyway.  

What is the best way to back up my data?  Is it a matter of backing up everything in my Home directory(s)?  The part that I am unsure of is backing up Evolution data and Firefox bookmarks.

Chris

---

### Post by beta.tester on 2010-04-15
> **cjwescott said:**
> I did what I could in uninstalling programs and that is where I got down to needing another 560 mb.  With regards to removing other kernels I removed them all.  Of the latest kernel that I am still using I did not delete the image file.  This is 120mb or so.  Even if I could delete this it would not be enough.

Clean install is starting to make the most sense so that I can increase the Root.  Plus it would be nice to start fresh anyway.  

What is the best way to back up my data?  Is it a matter of backing up everything in my Home directory(s)?  The part that I am unsure of is backing up Evolution data and Firefox bookmarks.

Chris

Hi Chris

A few ideas and hopefully solutions for you :)

1) For Firefox: Grab Xmarks (add on for Firefox, it saves passwords also if you want it to). Firefox => tools => add ons , search for Xmarks install and configure. When you reinstall Firefox or install it on another machine, xmarks allows you to import that selected data for your bookmarks/ passwords etc..

2) For Evolution: Easy Peasy :) Evolution => Files => Backup settings :) It creates a evolution-backup.tar.gz file (normally in /home) and it also contains all your messages, contacts and email pop and smtp setting etc... I find it invaluable. Save the evolution-backup.tar.gz file to somewhere safe ie cd, ram drive etc.. also remember to update it when you have a few more messages :)

3) To backup home the simple way. Use either an external hdd or decent size ram pen drive. Load the ram drive and open it, then simply open your Places => Home folder and CTRL-A and copy to the ram drive :)

Hope this helps.

Keep on Ubuntuing, and kind regards     john

---

### Post by uRock on 2010-04-15
> **beta.tester said:**
> Hi Chris

A few ideas and hopefully solutions for you :)

1) For Firefox: Grab Xmarks (add on for Firefox, it saves passwords also if you want it to). Firefox => tools => add ons , search for Xmarks install and configure. When you reinstall Firefox or install it on another machine, xmarks allows you to import that selected data for your bookmarks/ passwords etc..

2) For Evolution: Easy Peasy :) Evolution => Files => Backup settings :) It creates a evolution-backup.tar.gz file (normally in /home) and it also contains all your messages, contacts and email pop and smtp setting etc... I find it invaluable. Save the evolution-backup.tar.gz file to somewhere safe ie cd, ram drive etc.. also remember to update it when you have a few more messages :)

3) To backup home the simple way. Use either an external hdd or decent size ram pen drive. Load the ram drive and open it, then simply open your Places => Home folder and CTRL-A and cope to the ram drive :)

Hope this helps.

Keep on Ubuntuing, and kind regards     john
Very good ideas. My .mozilla and .thunderbird folders are 400MB.

---

### Post by Slim Odds on 2010-04-15
How big and how many hard drives?
How are they partitioned?
What is using up your disk space?

We need some details....... otherwise it's just wild guessing....

---

### Post by cjwescott on 2010-04-15
My apologies if I was vague or left out important information in my question(s). 
 
John (beta.tester) your suggestions are perfect for what I need or would like to do.  I have a portable HD and will do as you suggest. 
 
Thx for the tips!
 
Kind regards,
Chris

---

### Post by beta.tester on 2010-04-16
> **cjwescott said:**
> My apologies if I was vague or left out important information in my question(s). 
 
John (beta.tester) your suggestions are perfect for what I need or would like to do.  I have a portable HD and will do as you suggest. 
 
Thx for the tips!
 
Kind regards,
Chris

Hi Chris

You are more than welcome, any other problems let us know and we will do our best to help resolve them. I have found the people in here great at helping each other out (Could be why I like Ubuntu so much :)

Keep on Ubuntuing and kind regards    john

---

### Post by cjwescott on 2010-04-16
I downloaded the 10.04 Beta 2 Iso file.  Created a CD.  Booted off the disk, and it just hangs up in the end with the Ubuntu purple screen with all 5 (or so) dots all lit up.

When I view the contents of the CD, it all looks appropriate.

What am I doing incorrectly?

Chris

---

### Post by cjwescott on 2010-04-27
Well I finally got 10.04 RC installed.  Very painful. So painful I have to wonder how stable it will be with all the packages it said it couldn't install on the first pass and hopefully they all installed through the update manager.

Now the dilemma I am in:

I created a backup file for Evolution both for my account and my wife's account.  Mine restored fine, however my wifes did not.  It is saying that the back file in not valid.  What!!!!!  How can I make use of the file and get her data restored?

Any assistance is greatly appreciated!

Chris

---

### Post by Slim Odds on 2010-04-27
Not sure how to solve your problem, but please start another thread so that people will be able to find this topic and help you.

---

