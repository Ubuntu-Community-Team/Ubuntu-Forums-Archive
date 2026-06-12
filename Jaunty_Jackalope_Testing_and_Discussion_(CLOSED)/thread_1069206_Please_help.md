---
title: "Please help"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jman6495 on 2009-02-13
Right ,so here's what i did...
i downloaded the frostwire p2p software and it wouldn't work ,It Said I didn't have access to the folder so (not thinking because i had had a load of problems with windows earlier) And Changed My ENTIRE Home directories Permissions with root nautilus (overriding all) And so it for an unknown reason screwed my pc

anyway ... i managed to get the permissions back.but occasionaly My nautilus displays no titlebars , firefox won't load and all sorts of weird things happen...


  anyone have any idea what i have done

         Jman6495?!?!?!?!?!?!?!?!?!?!?!?!?!

p.s : ubuntu should have a tool to recover system permissions to default :-)

i can't say the amount of times i've screwed up the linux file permissions

---

### Post by Alterax on 2009-02-13
go to the terminal.

Use this command, replacing "yourusername" with what your actual username is:

```
sudo chown -R yourusername:yourusername /home/yourusername
```

---

### Post by personjerry on 2009-02-13
As a side note, try to make your thread titles more descriptive next time.

---

