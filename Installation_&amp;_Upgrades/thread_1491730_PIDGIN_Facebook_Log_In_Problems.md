---
title: "PIDGIN Facebook Log In Problems"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by sanoelk on 2010-05-23
I have successfully installed Pidgin (2.7) and added the Pidgin Facebook Plug-in (1.65). The problem is when I added my Facebook account to Pidgin, it says that that it is disabled and and gives "Invalid username or password." I have re-entered my my username and password several times carefully, but it always gives the same result.

So I tried setting up my Facebook Chat account using XMPP, but it gives me the same error.

Any ideas on how I can resolve this? Thanks.

---

### Post by sanoelk on 2010-05-26
I was able to solve the log in problem by completely uninstalling Pidgin and the Facebook Plug-in and re-installing them. 

I'm able to connect now, but the problem is, after a few seconds of being connected, the Buddy List window turns gray and becomes unresponsive. When I try to close it, it gives me the options to Force Quit, so I select that.

I already tried this:

sudo apt-get remove --purge pidgin
rm -rf ~/.purple
sudo apt-get install pidgin

But that didn't help.

I uninstalled the Facebook Plug-in, and Pidgin worked okay. So I guess it's a problem with the plug-in. I tried to install the older version of the FB Plug-in (which is the 1.4.x), but it keeps disconnecting from FB saying things about SSL, etc.

Can someone help me here?

---

