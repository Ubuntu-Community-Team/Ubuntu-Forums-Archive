---
title: "Limiting to line or Page"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by krsnavan on 2008-06-29
It's a basic question!

When i run command in commandline, i want to see the result in a page or line by line.( limiting scrolling)

for example:

ps ax 

to see the proccess running.

thanx

---

### Post by sdennie on 2008-06-29
It sounds like you want to use "more":

```

ps aux | more

```

Related commands are "head" and "tail":

```

cat some_file | head

```

Will show you the first few lines of the file.

```

cat some_file | tail

```

Will show you the last few lines of a file.

---

### Post by krsnavan on 2008-06-29
Ya!

that's what i asked. 

thanx

---

