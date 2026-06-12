---
title: "Apt-get woes after upgrade to Feisty..."
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by FlyingIsFun1217 on 2007-06-03
Hey!

My upgrade to Feisty went flawlessly on my laptop, but it seems on my desktop when I try and use apt-get now, I just get the following message (for everything), making it's use nothing at all...:

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package sharpconstruct-0.12-1sbx needs to be reinstalled, but I can't find an archive for it.'

Bummer.

Anybody have any suggestions?

Thanks a ton!
FlyingIsFun1217 :)

---

### Post by FlyingIsFun1217 on 2007-06-05
A...aa...anybody?

FlyingIsFun1217

---

### Post by zvacet on 2007-06-06
```
ssudo apt-get --purge remove sharpconstruct-0.12-1sbx
```

---

### Post by zvacet on 2007-06-07
Now I see that I mistyped command.it goes like this

```
sudo apt-get --purge remove sharpconstruct-0.12-1sbx
```

But I belive You understand my mistake allready.Sorry.

---

### Post by FlyingIsFun1217 on 2007-06-12
> **zvacet said:**
> Now I see that I mistyped command.it goes like this

```
sudo apt-get --purge remove sharpconstruct-0.12-1sbx
```

But I belive You understand my mistake allready.Sorry.

Sorry for not responding sooner. Been busy :/

Here's it's response:

> E: The package sharpconstruct-0.12-1sbx needs to be reinstalled, but I can't find an archive for it.

So... same thing as before :(

Thanks!
FlyingIsFun1217

---

