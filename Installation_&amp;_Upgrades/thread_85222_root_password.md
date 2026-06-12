---
title: "root password"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by paparucino on 2005-11-02
Hi guy,
I beg your pardon if this is a FAQ but this is my first approach to ubuntu.
I've installed the 5.04 release and now I'm downloading the 5.10.
Well, I like to login as root but I'm not able to do it since during installation the tool didn't asked me for a root password.
What is the correct way to set it?
Thank you

---

### Post by Hinko on 2005-11-02
Type:```
sudo passwd
```

then first enter your personal password. After that you can enter the new root password.

You can now use ```
su
```

---

### Post by Teroedni on 2005-11-02
why do you want to run root?
Its much better the way it is;)

I dont know how to permant run root, but if you only need to run root for a while

Open terminal:
write
sudo su
and you will be root for ca 5 min i think

if you want to browse your files as root
write

sudo nautilus

Hope this helps

---

### Post by niko_ on 2005-11-02
you can also use: sudo -s -H
which would ask you for your password and give you root shell,
so you dont have to type sudo every bit..

---

### Post by 23meg on 2005-11-02
If you absolutely know what you're doing and want to login to Gnome as root, you still need to enable the "Allow root to login with GDM" option in System / Administration / Login Screen Setup / Security.

But don't do it. Doing things by becoming root isn't a good working habit; use sudo instead.

---

### Post by paparucino on 2005-11-02
Thank you.
But... with your suggestion will I be able to login as root when I power up?

---

### Post by niko_ on 2005-11-02
paparucino yea, if you have activated your root account, but as others told you it is not recommended login as root.

---

### Post by SickTwist on 2005-11-02
paparucino, the reason everyone is warning you not to log in as root is this: When you log in using the root account, *every* program you run has root priviledges meaning any program could potentially mess up the entire system if it has a bug or security hole. It is especially dangerous if you open an Internet browser as root.

One of Linux's great strengths is its fine-grained permissions system which protects users from damaging the system accidentally. Running all programs as root inhibits you from taking advantage of the security that permissions offer.

---

