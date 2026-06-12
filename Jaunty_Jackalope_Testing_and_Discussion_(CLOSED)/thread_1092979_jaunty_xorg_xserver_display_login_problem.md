---
title: "jaunty xorg xserver display login problem"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cornflake000 on 2009-03-11
greetings...

I've been running jaunty alpha5.  It runs without a hitch once I get logged in but getting logged in is a bit rough.

I am having a problem that I have seen once and a while on the forums where you get these error messages...

Your screen, graphics card and input devices could not be detected correctly.  You will need to configure them yourself.

Then you are directed to low graphics mode.  After which you get the message...

There already appears to be an xserver running on display:0.  The specified display number was busy, so this server was started on display:1.

Finally I get to the login screen.

Out of curiosity, I looked in /tmp and found an .X0-lock and an .X1-lock.  Why would I have 2 display locks?  I am only running one graphics interface and one monitor.  Since I am still testing out jaunty, I reinstalled and still have the same problem.  I have an installation of intrepid on the same machine that has never had this hitch.  Both installations are ltsp installs.

Looking over the internet for 3 days, I have still to find a solution that applies even though this kind of thing has come up since 2004 in several distros.

Anyone have any ideas?

Thank you ^2

---

### Post by Neo_The_User on 2009-03-11
This should be moved to Jaunty discussion. Tell a forum staff member to move this.

---

### Post by cornflake000 on 2009-03-11
Yeah your probably right but as I said this has come up in many different distros in ubuntu going back several versions and also suse redhat fedora... not just jaunty.

thanks for the advice....

---

