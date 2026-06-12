---
title: "/tmp/.X11-unix has suspicious ownership (not root:root), aborting"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by nihility on 2005-03-05
I have been using ubuntu for the past couple of weeks with no problems at all, however today the xserver locked up for no reason... so i ctrl+alt+backspaced to restart it, and it crashed again - so I rebooted.

Now when it starts up the xserver does not start and I get the message:

"X: /tmp/.X11-unix has suspicious ownership (not root:root), aborting."

I have tryed google searching and found a couple of related things, but they mention changing the permissions or deleting the /tmp/.X11-unix

But when I try to do this with sudo it says "Operation not permitted"

Any help would be greatly appreciated, thanks

---

### Post by alastair on 2005-03-06
Try going to single user mode :

init 1

Then delete the file :

rm -r /tmp/.X*

Then back to X mode :

init 5

---

### Post by Abilnet on 2005-07-01
I had exactly the same situation and lost X after Kernel update to 2.6.11 and could not boot Ubuntu with the new or old Kernel.

Found out, that the **/tmp/.X11-unix** -folder was causing the problem and tried to get rid of it by deleting it. No luck, permissions were messed up, even root was not able to delete it... as root I only got the error message: "Operation not permitted" 

I found the following way to get out of the tricky situation and got my X and Ubuntu up & running smoothly again:

**As root in _Recovery Mode_ of the working Kernel I did the following:**

# cd /
# mkdir tmp2; chmod 755 tmp2; mv tmp tmp_old; mv tmp2 tmp
# chmod 1777 /tmp

That way I ended up to a situation I have an empty /tmp -folder with proper permissions - and Ubuntu is running smoothly again!  :grin: 

Hope this will help others, too

Kari from Sunny Spain :)

PS. Thanks Tero from Codeon Solutions for your help during the night! [http://codeon.fi/](http://codeon.fi/) ...he found the solution for me

---

