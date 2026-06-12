---
title: "Problems with AMD graphics card after upgrading from 14.04 to 14.10"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2014-10-24
After upgrading to 14.10 this morning I have the following issues:

While I get the splash screen and the login prompts, after loggin in I cannot see the sidebar or the top menu bar. It look like the resolution is very low and the menu bar's may be not visible because of this.
Looking at the .xsession-error I get
* Error of failed request: BadRequest (invalid request code or no such operation)
   Major opcode of failed request:   155 (GLX)
   Minor opcode of failed request:   19 (X_GLXQueryServerString)
                                      :
                                      :
                                      :


The card is a Radeon HD 8570D from AMD

Any help would be appreciated.

Thanks

---

### Post by Mark Phelps on 2014-10-25
Did you have the restricted AMD drivers installed? If so, those are kernel version specific and upgrading to a new release "breaks" them.  You will have to remove them and reinstall them -- see the link for details: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by lister171254 on 2014-10-25
Yes, had the restricted drivers installed.

Will check the link and let you know how I go.

Thanks for the quick reply

---

### Post by lister171254 on 2014-10-26
Tried the link you suggested (and others), but nothing worked.

As this was an upgrade from a new install, I installed and then upgraded without touching drivers and everything works ok.

Thanks

---

