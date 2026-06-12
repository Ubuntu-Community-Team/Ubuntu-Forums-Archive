---
title: "Linux Mint root password for live session?"
date: 2014-11-25
forum: MINT
---

### Post by flaymond on 2014-11-25
Today, Is my terrible day with Linux Mint ...respectively. I cannot boot to any OS except using live session of Linux Mint that prompted for login that I never do! I'm trying to install linux mint this morning and everything went so bad..my purpose is to succeed in making booatble USB (worked) but FAILED when installing the OS!!! Do any of you know what is root password for linux mint qiana or alternative to pass the login menu??? :(  I really sad..so sad..and I will never to try change os other than Ubuntu Distributions....respectively.

* i really need help asap :'(

---

### Post by ajgreeny on 2014-11-25
Mint is just like Ubuntu and has no root account, therefore no root password; it uses **sudo *command*** with your user password, which assumes that you as a user are a member of the **sudo** group, which the first user made during installation will be by default.

This also assumes that the iso file you used was a good one, and the install medium (USB) was not corrupt in any way.

---

### Post by coffeecat on 2014-11-25
*Thread moved to **MINT**.*

If the live Mint session is prompting you for login credentials, then you likely have a bad burn or a bad ISO.

---

### Post by pqwoerituytrueiwoq on 2014-11-25
i think the password should be blank/null/empty/void

---

### Post by flaymond on 2014-11-26
All method not worked....my tecnique to solv this-

 - Borrow friend's laptop
- Download Ubuntu's .iso and install to USB
- Boot and install Ubuntu

- Done 


* It took a day just for finding root password.

---

### Post by buzzingrobot on 2014-11-26
Mint's live session boots directly to the desktop. No password requested or required. Nor does use of 'sudo' require a password in a live session.

---

### Post by coffeecat on 2014-11-26
@InterProg, please take heed of buzzingrobot's post. What buzzingrobot has said is true of Mint, Ubuntu and the Ubuntu flavours, such as Xubuntu and Lubuntu. Your posted "solution" was not a true solution, merely an avoidance of the problem that you encountered with the Mint USB. As stated before, you probably had a corrupted ISO or a corrupted USB.

And I'm sure you've been told this before: **Don't bother with the root account or setting a password for it in either Mint or Ubuntu**. Instead have a read of this wiki page: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) . You need to understand it.

---

