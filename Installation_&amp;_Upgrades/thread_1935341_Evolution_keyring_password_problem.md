---
title: "Evolution keyring password problem"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by scruffyeagle on 2012-03-04
I have a problem involving the keyring password in Evolution. Note, I never did anything in particular to actually set this item...

I'd installed Ubuntu v10.04 LTS 32-bit, and used Evolution for a while. Then, I decided I wanted a different Gnome login password for that user account. I changed it, and from that point on Evolution wouldn't just download my email. It served notice to me that my keyring password didn't match my Gnome login password, and made me type in the defunct password. It was a nuisance, but I figured it was also an extra level of security on the account. (If someone hacked in w/ my Gnome password, they'd have to do a 2nd level of hacking to get at my email services.)

I've been experimenting w/ Linux variants; Kubuntu & Debian, so far. Debian also set up Evolution as the default email program. (Note, I used the same username & password in the Debian installation as what I'd used in the Ubuntu installation.) I did a backup of Evolution from the Ubuntu installation, and then did a restore in the Debian installation. It seemed to work perfectly. But, trying to download email in the Debian installation, I'm also getting the message about keyring password not matching the Gnome login password. The difference, is that nothing I type in allows me to download email; not the Gnome login password OR the Ubuntu installation defunct password.

Is there any procedure that will allow me to fix this password mismatch problem? TIA!

---

### Post by Vishal Agarwal on 2012-03-04
Did you configured the same user account in evaluation as the user account is ? Does the account is "user@localhost".

What is your user account name and what is the evolution user account name ?

---

### Post by scruffyeagle on 2012-03-06
_Vishal_: The ISP email account in Evolution and the Gnome desktop login account are different user names, and use different passwords. This is normal and beneficial, since Gnome desktop and Evolution email are 2 separate services. Beneficial, because the email account is the account involving an ISP. You wouldn't want a hacker who'd managed to invade your desktop system to also have gained immediate access to your ISP. So, these being different is a level of protection. The point of difficulty in my situation, involves the "keyring" maintained by the Evolution program. The keyring data is created by Evolution automatically during setup for accessing the ISP email. Part of the data it tucks away hidden, is the Gnome login password. I'm fairly sure the reason it does this is as a safeguard against being hacked from outside... Possibly as a safeguard against someone removing the hard drive from your computer and trying to access the Evolution data from a different machine; i.e., if the data doesn't match, and the user can't provide the correct data on the spot, then something's wrong and they shouldn't be allowed access.

NOTE: I thought this through after I posted my inquiry here, and came up with a partial solution. What I did was change the Gnome login password in the Debian installation to become the same as the defunct password I'd replaced in the Ubuntu installation. After I did this, the Debian installation of Evolution was able to download email from my ISP. There were a few error messages which I don't remember the details of, but once I'd acknowledged & closed the error message dialog boxes, Evolution downloaded email. I'll need to do another email session in the Debian installation, to see if this "fix" is still working.

However - this still doesn't resolve the original issue. I've also thought that through a bit, and have better defined what it is that I need to know:

How can one edit the keyring user data that Evolution tucks away & uses to verify the user?

---

### Post by scruffyeagle on 2012-03-26
In a nutshell, the reason for this inquiry is that after I changed the Gnome user's password, Evolution continually demands the user's password that existed when it was first set up, before it will download email. This is inconvenient - a continual annoyance.

I'ts been 2 weeks since I inquired, so I'm "bumping", hoping that someone will have an answer to this question:

How can one edit the data that Evolution tucks away & uses to verify the user?

TIA!

---

