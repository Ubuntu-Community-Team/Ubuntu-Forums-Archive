---
title: "Update probleme"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by arramis on 2016-08-08
Hello everyone,
When I'm thying to "sudo udate", I'm getting error in a terminal: 
A distorted row 1 in the Source list /etc/apt/sources.list.d/fullscreenprojpl.list (dist parse)
What should I do?

---

### Post by coffeecat on 2016-08-08
Post the terminal output of this command:

```
cat /etc/apt/sources.list.d/fullscreenprojpl.list
```

You can copy and paste the output from the terminal by highlighting the terminal output -> right-click -> copy, and then pasting into your post.

We can then see what is wrong in that file and someone will be able to help you solve the problem.

---

### Post by arramis on 2016-08-08
It is what I have in the file:
```
$ cat /etc/apt/sources.list.d/fullscreenprojpl.list
deb http://download.opensuse.org/repositories/home:/DarkSS:/deb/xUbuntu_14.04/ trusty

```

---

### Post by coffeecat on 2016-08-08
How did you add that third-party repository? Do you have a link to the howto?

Also, which version of Ubuntu or a derivative are you running? You have tagged the thread "kubuntu", whereas the repository appears to be for Xubuntu. And which release - 14.04, 16.04 or something else?

---

### Post by arramis on 2016-08-08
I've just installed Kubuntu 16.04 from kubuntu.org
And after this I was tying "update"
I didn't add repository

---

### Post by coffeecat on 2016-08-08
> **arramis said:**
> 
I didn't add repository

You have a source.list file for a 3rd party repository for the 14.04 version of Xubuntu with a malformed line. I very much doubt that the Kubuntu 16.04 ISO from a reputable download site would come with that. Although the fix is fairly straightforward, I am loathe to give advice where the information given doesn't seem to explain the evidence as shown. Something else could be missed.

For the information of anyone else who might wish to comment - and comments from Kubuntu users and those familiar with the Kubuntu 16.04 installer would be welcome - I found this which might be relevant:

```
http://software.opensuse.org/download.html?project=home:DarkSS:deb&package=fullscreenprojpl
```

**Edit**: sorry about that - either vbulletin or the opensuse server is playing up. If I make a hyperlink for that link, I get an error from the opensuse server. If you wish to view the page you'll have to copy-paste the link from the code box into your browser.

---

### Post by arramis on 2016-08-10
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]Thanks,
It helped, when string was repleced   ```
[COLOR=#000000][FONT=&amp]deb http://download.opensuse.org/repositories/home:/DarkSS:/deb/xUbuntu_14.04/ trusty[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][FONT=&amp]with[/FONT][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]```
deb http://download.opensuse.org/repositories/home:/DarkSS:/deb/xUbuntu_16.04/ /
```
I really don't now why it is Xubuntu, but it's true

---

### Post by coffeecat on 2016-08-10
> **arramis said:**
> I really don't now why it is Xubuntu, but it's true

That was my mistake. I thought that the "xUbuntu" was a strange way of capitalising Xubuntu. In fact, I think what they mean is that it is suitable for any flavour of Ubuntu, the 'x' being used as a wildcard.

However...

> **arramis said:**
> I've just installed Kubuntu 16.04 from kubuntu.org
And after this I was tying "update"
I didn't add repository

That sounds as though you are saying that you installed Kubuntu from an ISO you obtained from kubuntu.org and immediately tried to update and saw the error you quote in your first post. That is simply not possible, if the Kubuntu ISO genuinely came from a reputable source such as kubuntu.org. I've had a chance to discuss this with a Kubuntu user and they tell me that Kubuntu does not come with that 3rd party repository enabled. You claim that you didn't add a repository. Well, **someone** did. The fact that your installation contains a file with the filename /etc/apt/sources.list.d/fullscreenprojpl.list with the contents you have posted means that a 3rd party repository was added to your installation.

So... Did you do any additions or configurations between installing Kubuntu and getting that error? The reason I ask is that it is important to give the whole story if you want relevant advice.

---

### Post by arramis on 2016-08-10
I see you point. It was my mistake with "X", thank you for helping

---

