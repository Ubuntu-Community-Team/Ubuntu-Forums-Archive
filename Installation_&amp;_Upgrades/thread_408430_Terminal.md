---
title: "Terminal"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by udstuen on 2007-04-13
I'm trying to upgrade to Fiesty from Edgy.

Also...I'm still new so explain in as plain of English as possible.  The Update Manager fails to recognize that there is a need for an upgrade.  

I had to manually force the upgrade through the terminal last night

---sudo update-manager -c -d

It then asks for a password.  At that point, it will not let me enter ANY character from the keyboard...but I can still type anywhere else.

Weird...what should I do?

---

### Post by epiphiny on 2007-04-13
Not trying to be patronising, but are you sure that its not letting you input text, or is it just the fact that you don't get a line little ****'s appear?  You should get someting like:

sudo command
Password: 

Typing after Password: won't show any text, until you press return.

Sorry if partronising...

---

### Post by udstuen on 2007-04-14
If you hit enter after password, it returns to enter the next command.  You MUST enter the password as is.

I've tried every key on the board and nothing works.

---

### Post by aysiu on 2007-04-14
[quote=udstuen]I'm trying to upgrade to Fiesty from Edgy.

Also...I'm still new so explain in as plain of English as possible. The Update Manager fails to recognize that there is a need for an upgrade.[/quote] Since Feisty hasn't been officially released, wouldn't that explain the "failure" of the Update Manager to recognize the "need" for an upgrade?

---

### Post by aysiu on 2007-04-14
> **udstuen said:**
> If you hit enter after password, it returns to enter the next command.  You MUST enter the password as is.

I've tried every key on the board and nothing works.
It works. It just won't *appear* to work.

More info here:
[Feedback on entering password in the terminal?](http://ubuntuforums.org/showthread.php?t=214393&highlight=feedback+password+terminal)

---

### Post by udstuen on 2007-04-14
The only place I can't enter a password is in the Terminal password request section.

Also the color of the terminal changed from black to white from upgrading from Dapper to Edgy.

Anything?

---

### Post by aysiu on 2007-04-14
What people have been trying to tell you is that you **can** and should enter your password in the terminal, but you won't get any visual feedback or indicator that it's working.

Even though you can't see it working, it **is** working. Just type your password and hit *Enter*.

---

### Post by udstuen on 2007-04-14
Right....which is what I did.

It then tells me..."Sorry, try again." and asks for the password again.

Terminal NOT allowing text input in Password area!

---

### Post by udstuen on 2007-04-14
Le sigh...

Sometimes you're just having one of those days.

I entered the password....very....very...slowly.  Finally took and is now upgrading to 7.04.

Is there another upgrade beyond 7.04?

---

### Post by 23meg on 2007-04-14
> Is there another upgrade beyond 7.04?

Not at this point; even 7.04 is still in development.

---

### Post by aysiu on 2007-04-14
7.04's official release date is 19 April. It hasn't been released yet.

---

