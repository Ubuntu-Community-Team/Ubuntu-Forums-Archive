---
title: "help with apt-get: how to install package without prompting"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by bergamot on 2011-08-26
When I run 'apt-get install <some_package>' it asks you to enter configuration information for some packages.

I'd like to be able to install a list of packages automatically without having to enter any information, ie. an automated installation.

I looked in the man page for apt-get, and I was looking for maybe 2 possibilities:

1) tell it not to require input; I'll download the configuration files later

2) enter the options in the apt-get command.

I found what _might_ be what's required for option (2), the --option, but I found the instructions for using it not understandable. It says 'The syntax is -o Foo::Bar=bar', but I don't know where to go from there, and I'm not even sure it's relevant to what I want to do.

Can anyone advise? 

As an example, I want to install nslcd, and either sort out the configuration later (I have an ldap config file ready), or enter the ldap configuration along with the apt-get command. At present I have to enter the information interactively, which negates the possibility of an unattended install.

Many thanks

---

### Post by Kirboosy on 2011-08-26
Hi there!

I believe this command will do the trick

```
export DEBIAN_FRONTEND=noninteractive
```

then

```
sudo apt-get -q -y install <package_name>
```

It will assume &#8220;yes&#8221; to everything (and do it quietly)

**EDIT:**[Debconf]("http://manpages.ubuntu.com/manpages/natty/man7/debconf.7.html") is the name of the tool. That page should help you get going with everything you want to know.


~Caboose

---

### Post by bergamot on 2011-08-26
Yep, that seems to work. Thanks.

---

### Post by Kirboosy on 2011-08-27
Glad that worked. Could you please mark this thread as solved? 

Thanks
~Caboose

---

