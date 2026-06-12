---
title: "Unable to access a password on my ubuntu OS"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by noblegas on 2011-08-03
... when I tried to download an adobe flash player, this linux windows pops up saying that I should enter a password. When I entered a password(which was the password I used to log into my ubuntu linux operating system on my ibm think laptop), it says that the password is incorrect. I was under the assumption that the password that is required to download online applications and software like adobe(sudo password?) and the password that is required to log onto my operating system were the same passwords. What should I do to change the password that is needed to download online applications? I want to keep the password that is required to log onto my OS the same since I know that password.

---

### Post by noblegas on 2011-08-04
I think there is a main password and there is a root password . The main password is used to log into the operating system and then there is a root password that I need to download certain software applications such as adobe media player and a C compiler. I don't know the root password and I don't remember creating a root password before I bought my laptop whose harddrive contained a ubuntu linux operating system.

Do I need a boot CD? Because the operating system that came with the laptop I bought never came with any boot CD.

---

### Post by nothingspecial on 2011-08-04
There shouldn't be a root password.

Did you buy it from a company or privately?

Maybe your account is not an admin account. To fix this, reboot and enter recovery mode, type (get this right, if you miss the -a things will be worse)
```

usermod -a -G admin [COLOR="Red"]user[/COLOR]
```

You have to change the red user for the account you log in with.

Then type exit and boot normally.

---

