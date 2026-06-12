---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by FelipeAragao on 2011-02-20
When I run the 'sudo apt-get upgrade' I get the following output:
```
felipe@felipe-Inspiron-N5010:/$ sudo apt-get upgrade
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
2 pacotes não totalmente instalados ou removidos.
Depois desta operação, 0B adicionais de espaço em disco serão usados.
Você quer continuar [S/n]? 
Configurando python-sqlalchemy (0.6.3-2) ...
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/runpy.py", line 122, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.6/runpy.py", line 34, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.6/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.6/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.6/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 314, in <module>
    main()
  File "/usr/bin/pycompile", line 293, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 211, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: erro processando python-sqlalchemy (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 1
dpkg: problemas de dependência impedem a configuração de python-sqlalchemy-ext:
 python-sqlalchemy-ext depende de python-sqlalchemy (= 0.6.3-2); porém:
  Pacote python-sqlalchemy não está configurado ainda.
dpkg: erro processando python-sqlalchemy-ext (--configure):
 problemas de dependência - deixando desconfigurado
Nenhum relatório apport escrito pois a mensagem de erro indica que é um erro de seguimento de um erro anterior.
                          Erros foram encontrados durante o processamento de:
 python-sqlalchemy
 python-sqlalchemy-ext
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How can I solve this problem? Thanks!

---

### Post by sikander3786 on 2011-02-20
Try these commands and please post the outputs in English if possible.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by FelipeAragao on 2011-02-20
Thanks for the reply! This is the output:
```
felipe@felipe-Inspiron-N5010:/$ sudo dpkg --configure -a
[sudo] password for felipe: 
Configurando python-sqlalchemy (0.6.3-2) ...
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/runpy.py", line 122, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.6/runpy.py", line 34, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.6/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.6/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.6/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 314, in <module>
    main()
  File "/usr/bin/pycompile", line 293, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 211, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: erro processando python-sqlalchemy (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 1
dpkg: problemas de dependência impedem a configuração de python-sqlalchemy-ext:
 python-sqlalchemy-ext depende de python-sqlalchemy (= 0.6.3-2); porém:
  Pacote python-sqlalchemy não está configurado ainda.
dpkg: erro processando python-sqlalchemy-ext (--configure):
 problemas de dependência - deixando desconfigurado
Erros foram encontrados durante o processamento de:
 python-sqlalchemy
 python-sqlalchemy-ext

```
And...
```
felipe@felipe-Inspiron-N5010:/$ sudo apt-get install -f
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  geoclue libchamplain-0.4-0 libgeoclue0 librest-0.6-0 libethos-1.0-0
  libchamplain-gtk-0.4-0 libethos-ui-1.0-0
Use 'apt-get autoremove' para removê-los.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
2 pacotes não totalmente instalados ou removidos.
Depois desta operação, 0B adicionais de espaço em disco serão usados.
Configurando python-sqlalchemy (0.6.3-2) ...
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/runpy.py", line 122, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.6/runpy.py", line 34, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.6/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.6/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.6/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 314, in <module>
    main()
  File "/usr/bin/pycompile", line 293, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 211, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: erro processando python-sqlalchemy (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 1
dpkg: problemas de dependência impedem a configuração de python-sqlalchemy-ext:
 python-sqlalchemy-ext depende de python-sqlalchemy (= 0.6.3-2); porém:
  Pacote python-sqlalchemy não está configurado ainda.
dpkg: erro processando python-sqlalchemy-ext (--configure):
 problemas de dependência - deixando desconfigurado
Nenhum relatório apport escrito pois a mensagem de erro indica que é um erro de seguimento de um erro anterior.
                          Erros foram encontrados durante o processamento de:
 python-sqlalchemy
 python-sqlalchemy-ext
E: Sub-process /usr/bin/dpkg returned an error code (1)
felipe@felipe-Inspiron-N5010:/$ 

```

ps: how can I change the output language?

---

### Post by FelipeAragao on 2011-02-21
Help me please!

---

### Post by sikander3786 on 2011-02-22
> **FelipeAragao said:**
> Help me please!
There was a Terminal command for exporting the text in another Language but sadly, I don't remember it now.

Can you please switch your Language to English from System > Administration > Language Support and then post the outputs of those 2 commands.

---

### Post by FelipeAragao on 2011-02-22
I can't! It tells me that I have to install the language package, but when I try to, I get the sqlalchemy error. Damn! What can i do?

---

### Post by FelipeAragao on 2011-03-04
Can anyone help me? please! Perhaps I could try to translate it manually... though it wouldn't be like the original.

---

### Post by Skaperen on 2011-03-04
Google translate can help:

[http://translate.google.com/translate?hl=en&sl=pt&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1691845](http://translate.google.com/translate?hl=en&sl=pt&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1691845)

---

### Post by sikander3786 on 2011-03-05
Thanks for the help *Skaperen* :-)

@*FelipeAragao*:

Try to remove the offensive packages.

```
sudo apt-get remove --purge python-sqlalchemy python-sqlalchemy-ext
```

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

---

