---
title: "Error abriendo la cache (E:Malformed line 1 in source list /etc/apt/sources.list.d/ms"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by hidalgo23 on 2017-03-23
I have this error, i can not  find the problem....please help me

---

### Post by QIII on 2017-03-23
Hello!

Would you please post command and the entire text of the results?

---

### Post by hidalgo23 on 2017-03-23
E: Línea 1 mal formada en la lista de fuentes /etc/apt/sources.list.d/msprod.list (tipo)
E: No se pudieron leer las listas de fuentes.

---

### Post by hidalgo23 on 2017-03-23
i was trying to install sql server in my ubunto

---

### Post by QIII on 2017-03-23
Please post the command you are using and the entire text of the results.

---

### Post by hidalgo23 on 2017-03-23
bernal@bernal-Aspire-E5-471:~$ sudo apt-get update
[sudo] password for bernal: 
E: Línea 1 mal formada en la lista de fuentes /etc/apt/sources.list.d/msprod.list (tipo)
E: No se pudieron leer las listas de fuentes.
bernal@bernal-Aspire-E5-471:~$

---

### Post by hidalgo23 on 2017-03-23
[COLOR=#000000][FONT=Ubuntu]Error abriendo la cache (E:Malformed line 1 in source list /etc/apt/sources.list.d/ms.prod.list(type),E: the list of sources could not be read)
this other message is in the top of the windows  in a symbol red with a line  white..

[/FONT][/COLOR]

---

### Post by QIII on 2017-03-23
What instructions did you follow?  That source does not look right.

---

### Post by hidalgo23 on 2017-03-23
[https://www.youtube.com/watch?v=OqsOdUNsO4g](https://www.youtube.com/watch?v=OqsOdUNsO4g)
i was trying to do this

---

### Post by QIII on 2017-03-23
Why not follow [Microsoft's instructions]("https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu")?

However, I'm not sure why you would need to install MS SQL Server.  Is this for a particular purpose?

---

### Post by hidalgo23 on 2017-03-23
yes, i need it,

---

### Post by hidalgo23 on 2017-03-23
because i need it

---

### Post by QIII on 2017-03-23
OK.  I would remove the source you added and follow the instructions from Microsoft rather than a random YouTube video.

Let us know if you have problems with the official instructions!

---

