---
title: "New software udpate applet causes errors"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by melomonster on 2010-05-25
Hello! Recently i noticed there is a new software update applet (don't know how it got there; probably while updating software with default ubuntu applet). It looks cool and simple but every time i click on icon (that informs me that there are new updates) i got this error: 


```

Wyst&#261;pi&#322; niespodziewany b&#322;&#261;d (Unexpected error has occured)
Prosz&#281; zg&#322;osi&#263; ten b&#322;&#261;d w systemie &#347;ledzenia b&#322;&#281;dów dystrybucji, do&#322;&#261;czaj&#261;c opis b&#322;&#281;du (Please report this error to the  bug tracking system of the distribution, attaching error descrition)

Error Type: <type 'exceptions.UnicodeDecodeError'>
Error Value: 'ascii' codec can't decode byte 0xc5 in position 30: ordinal not in range(128)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in <module>
    main()
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
    run(args, options.single)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
    backend.dispatcher(args)
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
    self.dispatch_command(args[0], args[1:])
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 569, in dispatch_command
    self.get_repo_list(filters)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1082, in get_repo_list
    comp.name)

```The same error occurs when im using applet "Add/Remove applications". How do i get rid of this ?

---

