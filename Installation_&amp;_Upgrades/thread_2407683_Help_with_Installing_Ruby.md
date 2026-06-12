---
title: "Help with Installing Ruby"
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by talkingtree2 on 2018-12-07
Hi,

Does anyone know how to solve this? I'm trying to follow the instructions here, however, stuck at it, not sure which step am I doing wrong.

The key and bash seemed to work. However, at the step of 

```
Now install Ruby 2.3.4

source ~/.rvm/scripts/rvm rvm install 2.3.4
```

Getting this error

[IMG]https://i.imgur.com/JgKB9Lx.png[/IMG]

```

[h=5]5) Install Ruby[/h][COLOR=#6D7683][FONT=Lato]You will need to use the  version 2.3.4 based on their documentation (This version, may change, I suggest you to check their [requirements page]("https://github.com/sharetribe/sharetribe#installation") first.)[/FONT][/COLOR]
[COLOR=#6D7683][FONT=Lato]To ease our job, we will use RVM[/FONT][/COLOR]

[LIST]
[*]First, import the GPG key (under your regular user)
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3

[*]Then, install the latest version of RVM
curl -sSL [https://get.rvm.io](https://get.rvm.io) | bash -s stable

[*]Now install Ruby 2.3.4
source ~/.rvm/scripts/rvm rvm install 2.3.4
[/LIST]
[COLOR=#6D7683][FONT=Lato]This will download and compile ruby-2.3.4 for your system. It may takes some time depending on your bandwidth and computer speed[/FONT][/COLOR]

[LIST]
[*]Install the rubygems by running:
rvm rubygems current

[*]And ensure you are using the Ruby version 2.3.4 (needed if you have different Ruby versions installed on your server)
rvm use 2.3.4
[/LIST]

```

---

### Post by TheFu on 2018-12-07
I've been away from ruby development a few years, but I think you just need to separate the commands.
```

source ~/.rvm/scripts/rvm 
rvm install 2.3.4
```

---

### Post by talkingtree2 on 2018-12-09
> **TheFu said:**
> I've been away from ruby development a few years, but I think you just need to separate the commands.
```

source ~/.rvm/scripts/rvm 
rvm install 2.3.4
```

Hmmm, still getting the same results

[IMG]https://i.imgur.com/lEY0O1L.png[/IMG]

Below is the other method when entered the whole process.

[IMG]https://i.imgur.com/wUMP3av.png[/IMG]

---

### Post by TheFu on 2018-12-09
a) Please post text, not images. Also, use "code tags" like I have above.  Many people here pay for internet by the byte.
b) Don't use the root account for software development.  There will be issues.  sudo/root should only be used for administration tasks. Nothing else.
c) read the output from the commands. Text would be easier to quote. Those lines provide the needed information for the problem. Validate the group membership is correct for your development userid.

I've never installed ruby development tools as root, rather always used my development userid. Because of that, the tools were always installed under the userid HOME directory.  It isn't like any ruby web-app would be run as root.

Hope this is helpful.

---

