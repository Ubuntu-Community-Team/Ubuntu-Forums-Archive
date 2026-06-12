---
title: "Problems with safety repositories on having installed Kubuntu."
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by agente2012 on 2006-10-17
During the installation the system gives a mistake: " it is not possible to load the safety repositories " Then once already installed, the operative system not to be able to get up-to-date. The Adpt (Manager of packages) does not recognize the repositories, though these same are activated they do not want to connect. Also try(mean) for for Terminus(Terminal) (Konsole) Com the command " apt-get update " and one could not connect to ningun repository. The message of mistake was: it is not possible to connect to the servant. And in spite of this the mariner(browser) works perfectly. For ende there is Internet connection. It(he) is rare(strange) enough since the repositories are corectos. Because it there verifies with repositories of my another PC that which(who) works perfectly.:confused: 

[B]My computer is one:

Dell Optiplex 
I shape: GX 150 
Pentium the III
Ram 128MB + 256MB=386MB RAM 
Card of video integrated:-k[/B]

---

### Post by aysiu on 2006-10-17
Can you post (not just summarize) the exact output of these two commands? ```
sudo aptitude update
cat /etc/apt/sources.list
```

---

### Post by agente2012 on 2006-10-18
](*,) :( When I put the command "[B]sudo aptitude update
cat /etc/apt/sources.list[/B]"  Says following mistake: And: The order "update" does not take arguments:

And if I put only the command: "**sudo aptitude update**" it creates Me quite normally .... but when it goes to connect it does not want to connect..:-k 

And it is with new facilities... Because other persons estan having the same problem .. when they install kubuntu in these days... The reason to this failure(judgement) can be the servant for new users not this one working correctly? :-k

---

### Post by agente2012 on 2006-10-18
Already I tested with the following commands to see if the problem was solved:
[B]
"apt-get update" 
"apt-get  upgrade"
"apt-get dist-upgrade"
"sudo aptitude update"
"sudo aptitude update cat /etc/apt/sources.list"[/B] 

But the commands previously mentioned did not solve the problem. The system does not want to connect to the servants of update, but my another computer that also has Kubuntu 6.06 LTS (Dapper), the repositories if they him work and it gets up-to-date without problems. Does someone know really to which this problem owes?

---

### Post by aysiu on 2006-10-18
Can you please post the output as is?

It may be easier to diagnose the problem from the output than from your summaries of the output.

By the way, what I gave you was not one command. It was two commands: ```
sudo aptitude update
``` ```
cat /etc/apt/sources.list
```

---

### Post by tenzos on 2007-01-06
apparently i am suffering from the problems than agente2012, namely: good web connection but unable to connect to any repository.
here is my output of requiered commads:
[COLOR="Blue"]santi@santi-laptop:~$ sudo aptitude update
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) edgy Release.gpg
  No pude conectarme a es.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  No pude conectarme a security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  No pude conectarme a archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) edgy/main Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-es
  No pude conectarme a security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-es
  No pude conectarme a archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
0% [Conectando a es.archive.ubuntu.com (1.0.0.0)][/COLOR]

the other is similar: I dont like that IP 1.0.0.0 but I dont know the reason & I cant understand why the web goes ok.

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

