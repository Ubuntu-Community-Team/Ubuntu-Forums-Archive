---
title: "Strange sudo problem"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by Luke Redpath on 2005-06-24
[COLOR=Red]THIS PROBLEM IS NOW RESOLVED![/COLOR]

Hi,

I'm trying to set up a new Ubuntu server in our London office - one of the guys in the office has done the base installation and I can SSH into it using his username/password. Once in, I created a user for myself, added it to the admin group, logged out then SSHd back in using my own user account.

For obvious reasons I don't want to change to root to do everything, I prefer to use sudo only when needed. However, when I type:

sudo anyoldcommandhere

It rejects the password I enter.

However if I am logged in using the user account of the guy in the London office I can use sudo no problems with the same password so I know the password is correct.

Not just that, but when logged in as myself, I can switch to root by typing

su

Followed by the root password, and it works.

So why can I not use sudo when logged in as myself?

Cheers.

---

### Post by fdoving on 2005-06-24
[QUOTE=Luke Redpath]Hi,

I'm trying to set up a new Ubuntu server in our London office - one of the guys in the office has done the base installation and I can SSH into it using his username/password. Once in, I created a user for myself, added it to the admin group, logged out then SSHd back in using my own user account.

For obvious reasons I don't want to change to root to do everything, I prefer to use sudo only when needed. However, when I type:

sudo anyoldcommandhere

It rejects the password I enter.

However if I am logged in using the user account of the guy in the London office I can use sudo no problems with the same password so I know the password is correct.

Not just that, but when logged in as myself, I can switch to root by typing

su

Followed by the root password, and it works.

So why can I not use sudo when logged in as myself?

Cheers.[/QUOTE]
 Make sure you're in the group listed in /etc/sudoers as allowed to do sudos for all commands.

---

### Post by Luke Redpath on 2005-06-24
[QUOTE=fdoving]Make sure you're in the group listed in /etc/sudoers as allowed to do sudos for all commands.[/QUOTE]

Hi, from what I can tell, I am...here are the relevant parts:

/etc/sudoers
```

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

That is the default I think.

/etc/group (matthew is the username for our guy in london)
```

...
matthew:x:1000:
admin:x:109:matthew,luke
luke:x:1001:
...

```

---

### Post by fdoving on 2005-06-24
[QUOTE=Luke Redpath]Hi, from what I can tell, I am...here are the relevant parts:

/etc/sudoers
```

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

That is the default I think.

/etc/group (matthew is the username for our guy in london)
```

...
matthew:x:1000:
admin:x:109:matthew,luke
luke:x:1001:
...

```[/QUOTE]
 Hmm.. lookings correct.

You use your users password right? - You don't try to sudo with the root password or matthews password?

---

### Post by Luke Redpath on 2005-06-24
[QUOTE=fdoving]Hmm.. lookings correct.

You use your users password right? [/QUOTE]

Sorry, I'm having one of those days - for some reason I was entering the root password for sudo, not my own user password. Its working now. Thanks for your help - my own stupidity was the problem though! ;)

---

