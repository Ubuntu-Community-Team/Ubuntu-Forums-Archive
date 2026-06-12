---
title: "Ubiquity &amp; preseed user creation"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by wolverine_linux on 2008-12-02
I've been hacking at a preseed file for ubiquity and have been quite successful in achieving the results I wanted, except for one problem. I am trying to automate the non-root user account creation with the following entries in the preseed file:

```

# To create a normal user account.
d-i passwd/user-fullname string My Full Name
d-i passwd/username string myusername
# Normal user's password in clear text
d-i passwd/user-password password mypasswd
d-i passwd/user-password-again password mypasswd

```

This seems to work in so far as bypassing the user creation screen but in the next step which shows the summary and normally initiates start of the installation, the Install button is disabled.

I've also tried by supplied an MD5 encrypted user password (changing the commands appropriately of course) with no luck.

When I omit the password commands from the preseed file, Ubiquity shows me the user creation window with values provided pre-filled in the appropriate textboxes. It then asks for the password and confirmation. Once this is done, it then allows clicking on Install button in the summary window.

This seems to be the problem with GTK Ubiquity only, I've been able to install it successfully with the same preseed file using noninteractive mode.

Is anyone able to explain the problem or suggest a workaround?

---

### Post by wolverine_linux on 2008-12-04
It's me again, I've managed to find a workaround for the problem. Not exactly what I was hoping for but better then being unable to install at all.

Adding the following to the bottom of the preseed file makes ubiquity skip the last (confirmation) screen altogether. It installs as expected.

```
ubiquity        ubiquity/summary        note
```

I hope someone else finds this solution useful. I hope even more that someone fixes the actual problem.

---

### Post by paterick on 2010-05-05
It would work if "complete" was not set False in ./ubiquity-2.2.24/ubiquity/components/ubi-usersetup.py

I edited that file a bit to find out

Another workaround is to have the following in your preseed file:

```
d-i user-setup/allow-password-empty boolean true
```This lets you still click the install buton (you can check the summary)

Would be nice if somebody could report this to the developpers of ubiquity.

Cheers

Patrick

```

--- ./ubiquity-2.2.24/ubiquity/components/ubi-usersetup.py    2010-04-29 11:32:53.000000000 +0200
+++ ./ubiquity-2.2.24/ubiquity/components/ubi-usersetup.py.debug    2010-05-05 21:29:47.000000000 +0200
@@ -336,6 +336,10 @@
                 self.password_valid.hide()
                 complete = False
         else:
+            import sys
+            print >>sys.stderr, "complete was " + str(complete) +
+                " - passw|vpassw -> " + (passw and passwd or "NULL") +
+                                  "|" + (vpassw and vpass or "NULL")
             self.password_valid.hide()
             complete = False

```

---

