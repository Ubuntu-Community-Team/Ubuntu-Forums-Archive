---
title: "Need to reinit apt-get on 5.10 so i can upgrade"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Koobi on 2007-03-27
I've been using Ubuntu 5.10 at work and the other day, I didn't come to work and they had an issue with another linux PC...to make a long story short, a person who wasnt too aware of linux had, for some reason, compiled checkinstall by hand and done something and it seems to have messed up my package manager.

i want to upgrade my ubuntu but everytime i try to:
```

$ sudo apt-get update && apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
E: The package checkinstall-1.5.3 needs to be reinstalled, but I can't find an archive for it.

```


i don't know exactly what this person did...is there any way that i can reinitialize my apt-get?


any assistance would be greatly appreciated as this is quite urgent :(

---

### Post by diepruis on 2007-03-27
You might try: 

```

sudo apt-get remove checkinstall

```

---

### Post by Koobi on 2007-03-27
thanks for the reply.

i already tried that. i also tried to purge and reinstall, i tried fix-broken as well but nothing worked.

it seems like my only option is to either reinitialize the apt db or recreate the config files but i'm unaware of how to do it the proper way.

---

### Post by diepruis on 2007-03-27
What was the output from those commands?

---

### Post by Koobi on 2007-03-27
It's the same error as before:
```

E: The package checkinstall-1.5.3 needs to be reinstalled, but I can't find an archive for it.

```



he told me he had compiled checkinstall so that he could compile another program to install on my PC...i don't know why he didn't just use aptitude.

it seems that he had used the checkinstall source from the ubuntu archives to create a deb.
i think i've found the checkinstall deb that he used. so i tried this out:
```

# sudo cp /source/to/checkinstall.deb /var/cache/apt/archives
# sudo apt-get update && apt-get remove checkinstall

```
but it gives me the same error.

---

### Post by diepruis on 2007-03-27
If you haven't already, can you enable universe? And then please try the folowing:

```

sudo apt-get -m update
sudo apt-get -m purge checkinstall

```

See 

```

man apt-get

```

for more info on -m

I'm not sure whether this will work, but it looks promising from the man page.

---

### Post by Koobi on 2007-03-29
hi,
thanks for the reply. i had already tried the -m parameter earlier (sorry i forgot to mention) but it gives me the same error regarding not being able to find the archive.

---

### Post by diepruis on 2007-04-01
Mmmm...

What does

```

sudo apt-get check

```

tell you?

---

