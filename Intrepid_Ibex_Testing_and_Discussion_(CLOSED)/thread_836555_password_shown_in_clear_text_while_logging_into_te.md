---
title: "password shown in clear text while logging into terminal."
date: 2008-06-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by CrazyGuy123 on 2008-06-21
When I log into Ubuntu (or most other Linux systems), if I type the password too soon after the username the following happens:
```

Ubuntu intrepid (development branch) laptop tty1
laptop login: [COLOR="Red"]username[/COLOR]
[COLOR="Red"]sec[/COLOR]Password: 

Login incorrect
laptop login: 

```
(the issue is that the first few characters of the password, as shown in red, are in plain text on the terminal, and not used as part of the password input)

There are two issues here:
[LIST=1]
[*]It is a minor security problem if someone is looking over your shoulder
[*]It is annoying to have to type your username/password again simply because the system "missed" the first bit of the password the first time.
[/LIST]

I suggest the cause of the problem is the "login" process gets swapped to disk since it may not have been used for many weeks on server systems, and is only paged back from disk when the user presses enter after the username.  Also, characters entered before the password prompt are ignored since the getpass() function flushes the buffer before printing the password prompt.

As a solution, either we need to modify the login program to use a custom equivalent of getpass() which doesn't flush the buffer, or find some way to eliminate the delay sometimes seen between pressing enter and getting the password prompt.  Note that the paging from disk is only one theory about what could cause the delay - there are many other possible causes.

To reproduce the problem, switch to tty1 on a standard Ubuntu-desktop machine, leave it overnight, then try to login while touch typing.  The issue only seems to happen once per boot.

Should I file a bug report?  Can we fix this locally, or do we need to pass it upstream?  Do certified developers need to work on it since this is very security critical code?

---

### Post by CrazyGuy123 on 2008-06-21
as an offtopic aside:
At work sometimes we try to see who can type the most characters of the password correctly before the prompt appears.

---

### Post by Gina on 2008-06-21
Never had that myself - mind you I have a short user name that might make a difference.

---

### Post by MALEADt on 2008-06-21
I "suffer" from that "bug" quite a lot, but cannot see how you should fix it. Login over SSH has the same problem too.

---

### Post by Eclipse. on 2008-06-21
It happens when you start typing before the new line in the terminal is there.Its not really bug, just the reactiveness of your system.

---

### Post by CrazyGuy123 on 2008-06-21
Either way I think we can solve it by changing the call to getpass() in login.c so it doesn't discard the input buffer before asking for the password.  I see no real reason to discard the buffer anyway from a security point of view, either before or after password entry. Leaving the buffer intact will also alow faster logins on high latency terminals like ssh across the internet.

Also I wouldn't say it only occurs on old slow machines - counterintuitively, hardware spec doesn't seem to make any difference for me.  (Tried on an openWrt machine with 16 meg of ram via ssh with the same result)

---

### Post by Nullack on 2008-06-22
Id bug it for sure its an issue IMHO

---

### Post by soccerboy on 2008-06-23
I find this bug amusing too.  I try to type as much of my next command after my password.

---

