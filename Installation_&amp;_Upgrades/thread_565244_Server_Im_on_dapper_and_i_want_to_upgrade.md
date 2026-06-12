---
title: "Server: Im on dapper and i want to upgrade"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2007-10-02
Hello im on dapper 6.04 on my server . I use this server for backing up , and its a samba server. I was wondering what distro i should upgrade to. If i upgrade will it change any of my ip / samba settings. This is very important because if it does the whole buisness will go down

---

### Post by j.bunce on 2007-10-02
Dapper is supported until 2011, so in terms of updates etc your server will be supported. If you have things on your server like php and asp, these *could* break during an upgrade, depending on your configuration. Assuming you log into your server via SSH from a terminal, this is how to upgrade:

```
ssh user@yourserver
```

```
sudo sed -e 's/dapper/ edgy/g' -i /etc/apt/sources.list
```

then update:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Note: sometimes you must run sudo apt-get upgrade again, after performing the dist-upgrade.

Hope this helps,
jake

---

### Post by Seisen on 2007-10-02
Also if you changed any of your configuration files it should ask you when it install the new versions conf. file or leave it as is. I know it did this with cups so I would assume it should do this with other packages.

---

### Post by Soybean on 2007-10-02
I'd wait until next year before upgrading a Dapper server, at this point. The next LTS release is scheduled for April 2008, and I *believe* that it will be possible to update straight from Dapper to the new LTS release. So, if you want to get current right now, it's a 2-3 step process (2 for Feisty, 3 for Gutsy which comes out in a couple of weeks), where any of the 2-3 steps could potentially fail. If you wait until April, you should be able to jump right to the latest version in a single step.

Note that this is all based on my belief that they plan to provide a straight 6.06->8.04 upgrade path, which I'm sure I read somewhere, but can't find a source for at the moment. :???:

---

