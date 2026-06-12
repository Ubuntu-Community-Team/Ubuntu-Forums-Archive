---
title: "Cant Login to Ibex after package Updates"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by balla786 on 2008-10-15
So I did a fresh install of Intrepid Ibex Beta that I downloaded and burned today.

It installed wonderfully.  It's superb thus far, everything working right away, couldn't be happier (perhaps when the final released is out).

I did some recommended system updates from the update manager.  Rebooted the computer.  It hung up shutting down until I took out my lan cable.  Finally restarted and ended up getting Grub again, choosing the default, and instead of loading the familiar logon gui, it went to a Dos window, which basically asks me to authenticate with my username and password.  I have no idea what I'm doing there other than logging in with my credentials.

Any ideas how to get my normal logon window?  I'm suspecting it was an update that caused it, but I'm not sure what.  Anyone else having the same issue?

Thanks!

---

### Post by marttali on 2008-10-15
Most likely something went wrong with the update and your xorg.conf has problems.
You can try to reboot again and while grub is loading you have to push del or esc, cant remeber which one right now and then you must choose latest kernel with recovery mode.
You will get a nice blue screen with some options where you then should choose xfix. That thing tries to fix your dispaly problems.
After that resume normal boot.

---

### Post by jerrylamos on 2008-10-15
In my case least time wasted & frustration was to re-install original NOT UPDATED beta.

If you want updates, then rsync download a newer level of beta and see if CD Live works.  In my case it doesn't, same hang that the updated beta got.

When/if CD Live works, I'll install it to get whatever updates it has.  

Jerry

---

### Post by balla786 on 2008-10-15
I'll try those suggestions.  If it doesnt work, I'll just reinstall and do some selective updates.  Go from there.

If anyone has any other suggestions, keep em coming!

Thanks.

---

### Post by PopOmatic on 2008-10-15
This is something that has happened for me already few times after updates - I get only black screen. I think it is somehow Kernel related, but I am not really sure how.

What ever it is selecting recovery mode from grub and "fixing Xorg" has worked every time this has happened.

---

