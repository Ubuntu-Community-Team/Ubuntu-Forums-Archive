---
title: "can't log in to Ubuntu Core 16 on Raspberry Pi 3"
date: 2017-03-24
forum: Installation &amp; Upgrades
---

### Post by jakpowpbs on 2017-03-24
I am unable to log in to Ubuntu Core 16 using a Pi 3, I have followed [https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3](https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3) but get stuck on localhost login after going through the network and admin config.

I have imported the public key onto my sso account and tried every possible format to log in with, on the pi as well as remotely using [B][FONT=Courier New]ssh <Ubuntu SSO account name>@<device IP address>.

[/FONT][/B][FONT=Courier New]getting: **login incorrect** on the pi and **access denied** whilst trying remotely through PuTTY.

[/FONT][FONT=Courier New]Any ideas? thanks[/FONT]

---

### Post by koolinus-gmail on 2017-05-15
I am having this exact problems two months later&#8230; help would be welcome, thanks!

---

### Post by Bucky Ball on 2017-05-15
Welcome. The login for a RPi is generally 'pi' and the password is generally 'raspberry'. Tried that? Just a suggestion. 

Also, while your problem might look identical on the surface, it's probably not. You should be posting another thread as this one was started by someone else. Good luck. :)

For instance: Ubuntu Core 16 using a Pi 3. Is this you? 

[QUOTE=jakpowpbs]I have imported the public key onto my sso account and tried every possible format to log in with, on the pi as well as remotely using ssh <Ubuntu SSO account name>@<device IP address>.

getting: login incorrect on the pi and access denied whilst trying remotely through PuTTY.[/QUOTE]

Have you done exactly the same and are getting the same error message? There is no reason whatever for the above fiddling with SSO passwords, by the way. Not sure how it's related to the problem of the user/pw not working on a RPi. The username and password should work, if correct, with no further twiddling from the user required.

---

