---
title: "Login request on upgrade to 11.04"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by n08rak35 on 2012-01-03
Hi folks. 

I have been running Ubuntu on my laptop for a couple of years now without any major problems, and with a lot of good successes.

However, I did not realise that LTS was selected in the update manager and therefore I was still using lucid, which is a number of versions old. So I upgraded through the update manager twice but now (I am up to 11.04) I can't login.

On rebooting the computer during installation, I get:

Ubuntu 11.04 splash screen

black screen

Then a list of tests followed by the message:
"Ubuntu 11.04 [computername] tty1

[computername] login:"

This is strange, mainly because I don't use a password on my computer. I am the only user and don't use the login screen, so I don't think I have ever set a user name. I have a password which I use for upgrades etc.

Nothing I have tried gets me past this screen. Either login comes up again, or I get an "Incorrect Password" message.

I hope someone can help! ](*,)

---

### Post by ottosykora on 2012-01-03
well during the intial installation you were asked to enter a user name and password for it.
This would the one you should enter here.

But, otherwise all looks kind of strange as it should go to boot with the GUI and this is a login into the command line (terminal)

---

### Post by n08rak35 on 2012-01-06
The best advice I found was to go back kernel by kernel to find a build that worked.

I did that by pressing esc at the appropriate time (Grub loading) and then chose the second last kernel. This allowed me to boot the computer a number of times without trouble. 

I then went to the upgrade manager again and moved on to the next upgrade and this solved the problem of the login.

By the way, I found my user name when I managed to logon and this was still not accepted by the logon request - obviously an in between build bug.

Now to find out if is was all worth it.... I kind of liked my old Ubuntu....not so sure about the new one....

---

