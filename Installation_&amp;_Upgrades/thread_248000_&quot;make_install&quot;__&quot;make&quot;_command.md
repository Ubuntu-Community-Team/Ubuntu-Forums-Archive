---
title: "&quot;make install&quot; : &quot;make&quot; command not found"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by kolobaki on 2006-08-31
&#919;&#921; in all. As I write and in the title this command in Dapper it doesnt  work.maybe exists another command in order to I make compille?
THANKs

---

### Post by x64Jimbo on 2006-08-31
you need this package:
build-essential

---

### Post by tommyg on 2006-08-31
```
sudo apt-get install build-essential
```

---

### Post by x64Jimbo on 2006-08-31
Just use the package manager. The command line method is outdated and unnecessary now. Plus, aptitude is better at dependency management than apt-get anyway.

---

### Post by kolobaki on 2006-08-31
thanks a lot

---

### Post by angkor on 2006-08-31
> **x64Jimbo said:**
> The command line method is outdated and unnecessary now.

It is? What if you want to update / upgrade a box without X? Or X on your desktop is broken? ;)

---

### Post by hizaguchi on 2006-08-31
> **angkor said:**
> It is? What if you want to update / upgrade a box without X? Or X on your desktop is broken? ;)
Not just that, but who wants to wait for Synaptic to load up every time you need to install an app?

---

### Post by x64Jimbo on 2006-09-03
You know, we could go back and forth about this till we're blue in the face. Synaptic is an amazing tool, and telling our new users to use the command line to install apps is like walking around telling people to stop using computers and switch to typewriters because they don't have any boot-up time. How would the Synaptic devs feel if they saw all the hard work they've put in go to waste?

---

### Post by angkor on 2006-09-03
> **x64Jimbo said:**
> You know, we could go back and forth about this till we're blue in the face. Synaptic is an amazing tool, and telling our new users to use the command line to install apps is like walking around telling people to stop using computers and switch to typewriters because they don't have any boot-up time. How would the Synaptic devs feel if they saw all the hard work they've put in go to waste?


[offtopic]
I wasn't telling anybody what to use. I agree Synaptic is a great tool, yet so is apt (or aptitude). I simply wanted to point out that your comment that "the command line method is outdated and unnecessary now" is not true, because both Synaptic and Apt(itude) have their use in different situations.
[/offtopic]

---

### Post by x64Jimbo on 2006-09-04
I didn't say that you told someone what to use. I know that it was tommyg. Point is that if we tell our new users to use the command line to install software, they'll miss out on the convenience that Synaptic has to offer, and we want to make Linux as easy and fun as possible. I know there are appropriate times to use the command line tool. But if someone asked how to burn a CD, you wouldn't tell them to open a command window and type 
```

cdrecord dev=/dev/hdb [filename]

```
would you?

---

### Post by taurus on 2006-09-04
What's wrong with command line?  Everyone needs to know how to use it...  :rolleyes:

---

### Post by x64Jimbo on 2006-09-04
Yes, but they **only** need to use it when they **can't** use synaptic. If we always give them the command, they won't know how to do it for themselves! They'll just copy and paste the command and forget. Then next time they need an app or package, they'll have to go searching google about how to install, or worse, post the question to these already overloaded boards. I don't see how any of you can keep telling yourselves it's fine to proverbially give a man a fish to feed him for a day rather than teaching him how to fish to feed him for a lifetime.

---

### Post by sx75 on 2006-10-13
Using commandline is better if you manage systems what needs more security. Because if you run X application then there is more code what might have mistakes in.

---

### Post by x64Jimbo on 2006-10-13
A system that needs better security (a server) shouldn't have a GUI in the first place, but I still argue that using a program in a graphical environment doesn't make you any more vulnerable than  you already are by running the GUI in the first place. Synaptic doesn't listen for connections from the outside, so it is not a vulnerable point for network attacks. If the attacker doesn't have a login on your box (I hope he doesn't) he won't be able to run the program for the purpose of getting it to crash, which might allow him access to your system.

---

