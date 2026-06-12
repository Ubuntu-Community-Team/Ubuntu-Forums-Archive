---
title: "odd nautilus error"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2010-03-03
when issueing the following command in a terminal sudo nautilus
in get the following error

Nautilus could not create the required folder "/root/Desktop".
Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

Any ideas on how to fix it? running 64 bits all updates installed

---

### Post by cariboo on 2010-03-03
Open a terminal, then type:

```
sudo -i
```

this will drop you to /root, where you than create the Desktop directory:

```
mkdir Desktop
```

---

### Post by mdurham on 2010-03-03
> **lime4x4 said:**
> when issueing the following command in a terminal sudo nautilus

I think you should, for some reason, use 'gksu nautilus' I don't know if it would make any difference though.

---

### Post by lime4x4 on 2010-03-03
Won't let me make the dir

mkdir: cannot create directory `Desktop': File exists

---

### Post by alexmurray on 2010-03-03
Why do you want to run nautilus as root anyway?

If you want an easy way to open files as root from nautilus, you could just use something like this: [http://www.pendrivelinux.com/how-to-open-files-as-root-via-a-right-click/](http://www.pendrivelinux.com/how-to-open-files-as-root-via-a-right-click/)

---

### Post by VMC on 2010-03-03
> **mdurham said:**
> I think you should, for some reason, use 'gksu nautilus' I don't know if it would make any difference though.

That's the problem. The OP tried to find /root/Desktop using nautilus. If you instead use the above command 'gksu nautilus', you will see the root folder.

---

### Post by mc4man on 2010-03-03
> If you want an easy way to open files as root from nautilus, you could just use something like this
There is already a package for that available, (and probably preferable to running gksu nautilus

```
sudo apt-get install nautilus-gksu
```

(I'd be inclined to use the above to open /root and ck. the perm.'s of Desktop ( or do fron cli

---

