---
title: "Reinstall help needed from Live CD"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-01-01
I have a lot of problems with my 10.10 (Firefox and Opera freeze, boot sequence lost. I have to complete it manually)  and have decided it might be best to do a fresh install.

My system partition is sda1
Home is sda2


When I try to install from the liveCD into sda1, without formating,  it says 

*No root filing system is defined. Please correct from the partition menu. *

I do not know how to set up the root filing system from the liveCD as I can see no obvious option. Where is it?

Robin

---

### Post by presence1960 on 2011-01-01
> **Robbyx said:**
> I have a lot of problems with my 10.10 (Firefox and Opera freeze, boot sequence lost. I have to complete it manually)  and have decided it might be best to do a fresh install.

My system partition is sda1
Home is sda2


When I try to install from the liveCD into sda1, without formating,  it says 

*No root filing system is defined. Please correct from the partition menu. *

I do not know how to set up the root filing system from the liveCD as I can see no obvious option. Where is it?

Robin

Highlight the sda1 partition and click the "Change " button. Set mountpoint to " / ". personally I would tick the format box and format sda1.

Highlight sda2 and click "Change" button. Set mountpoint to "/home". **_Do not tick the format box or you will format sda2 and lose your data. make sure you set mountpoint to /home so your /home auto mounts when you boot ubuntu._**

Continue with the install.

---

### Post by Robbyx on 2011-01-02
The fresh install has not gone smoothly. Although I think I have used the correct user name and machine name in the fresh install, I do not know how to check what  I should have used  to replicate the original user name, machine name, and nick name.
When  I login in to the user I get the following error message:

/usr/lib/libconf2-4/gconf-sanity check-2 exited with status 256.

The machine then hangs as if it is is waiting for something. I can drop to the command line by CTRL ALT F1.

Assuming from my searches this is something to do with the home directory I have found its settings are:

drwx------

I have tried sudo chmod 700 /home/rob

It does not make the error message go away.

So far I have not been able to get into the desktop although I can access the  login screen.



Robin

---

### Post by Robbyx on 2011-01-02
As a temporary measure I have been able to add a new user. This has not had the same error message response on logging in. Nothing is set up the way it was before because it is a new user setup, but I can access the data drive, and the old home. The old home is not being used by the new user.

 I would like to get back to the old setup. Can you help me please?

Robin

---

### Post by Rubi1200 on 2011-01-02
Bug report:
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

See post #78 for a possible solution.

But also read the other information please.

Hope this helps.

---

### Post by Robbyx on 2011-01-02
I am getting into a tangle.

The new user: fred is showing as being logged in together with the old user rob. Thus 2 users are logged in a once although I have to choose one and its password to actually run it in the desktop.

rob has a home directory called /home/rob. All the files are now owned by fred.

If I login in as rob I get the error message. I do not get the error message with fred but fred does not load the old desktop settings.

I could try to use only fred but that will give me a lot of problems with setting up the apps. I would prefer to have rob working properly.

Robin

---

### Post by Robbyx on 2011-01-02
I am getting into a wonderful mess:

Created a new user mike and pointed him at the old home of rob. He starts but there are no desktop panels.

I changed the permissions on ICEauthority and if I login as  rob and let rob use /home/rob no panels show, but it does not hang, as previously. It is just not useable because of the absence of panels or icons.

Fred starts ok and shows panels but none of the old settings I had for rob. Fred is using his own home/fred.



Robin

---

