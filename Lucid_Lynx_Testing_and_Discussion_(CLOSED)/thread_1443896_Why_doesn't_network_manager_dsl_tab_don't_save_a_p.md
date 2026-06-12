---
title: "Why doesn't network manager dsl tab don't save a password?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-31
i created a new profile in dsl wrote my user name and password and yet when i open it again it doesn't save the password why is that and what can i do about it?

thanks in advance.

---

### Post by cariboo on 2010-03-31
Are you using the same password in the keyring as your login password?

---

### Post by aviramof on 2010-03-31
it's my isp password and no of course not.

---

### Post by psyke83 on 2010-03-31
When I installed from alpha 2 or 3, NetworkManager was not able to save passwords to the "default" keyring, which meant that each time I had to enter the wireless password and then click "cancel" on prompts to save the password/access the keyring.

I managed to resolve the situation by deleting the re-creating the default keyring. Here's the steps:

[LIST=1]
[*]Go to: Accessories -> Passwords and Encryption Keys -> Passwords tab.
[*]Delete ALL keyrings listed (I believe at the time I performed these steps, the only keyring was named "default", but I see it now listed as "login").
[*] Click File -> New -> Password Keyring.
[*] Name the new keyring as "login" (although when I performed the steps, I named it "default").
[*] Use the same password as your user login password.
[*] Right-click on the newly created "login" keyring, and choose "Set as default".
[*] Log out and back in.
[/LIST]
  In my case, NetworkManager was then able to store wireless passwords properly.

You may want to wait until somebody more knowledgeable comments on this, because I'm not sure if this will have any adverse effects.

---

### Post by aviramof on 2010-04-01
i don't have anything in Passwords and Encryption Keysi disable it not long ago because empathy keep asking for password every time i opened it and that happen because i use auto login so it did not open the keyring at startup any way i chose unsafe there and that it and now there is nothing there.

and now when i try to create a new password i get this error messege "Error communicating with  gnome-keyring-daemon"

---

### Post by psyke83 on 2010-04-01
> **aviramof said:**
> i don't have anything in Passwords and Encryption Keysi disable it not long ago because empathy keep asking for password every time i opened it and that happen because i use auto login so it did not open the keyring at startup any way i chose unsafe there and that it and now there is nothing there.

and now when i try to create a new password i get this error messege "Error communicating with  gnome-keyring-daemon"

I don't mean to offend, but sometimes it can be quite difficult to understand what you're saying. Are you saying that there is no keyring listed at all, or that a keyring is listed which has no password?

Either way, whatever steps you took to "fix" Empathy have broken NetworkManager.

I suggest:
1. Disable auto-login (temporarily)
2. Create/Recreate the "login" keyring **with **a password (as I instructed before)
3. Set up your NetworkManager DSL connection. When it is working correctly, enable the checkmark "Available to All Users".
4. Enable auto-login.

---

### Post by aviramof on 2010-04-01
ok i have to say that i really don't understand this strange network manager i managed to save the password eventually but now i don't have the top panel icon and one more problem is that if i mark available for all users the profile i created simply disappears and i really don't understand it when does this profile go?

---

