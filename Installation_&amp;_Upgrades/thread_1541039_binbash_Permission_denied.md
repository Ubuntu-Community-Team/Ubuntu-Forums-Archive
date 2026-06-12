---
title: "bin/bash: Permission denied"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by p.matulionis@gmail.com on 2010-07-28
I have a problem using command sudo make check:
```

root@paulius-laptop:/var/www/Xaira# sudo make check
Making check in indexer
make[1]: Entering directory `/var/www/Xaira/indexer'
make  test-indexer
make[2]: Entering directory `/var/www/Xaira/indexer'
make[2]: Nothing to be done for `test-indexer'.
make[2]: Leaving directory `/var/www/Xaira/indexer'
make  check-TESTS
make[2]: Entering directory `/var/www/Xaira/indexer'
/bin/bash: line 8: ./test-indexer: Permission denied
FAIL: test-indexer
==================
1 of 1 test failed
==================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/var/www/Xaira/indexer'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/var/www/Xaira/indexer'
make: *** [check-recursive] Error 1

```

Can anybody tell why I'm getting this error?

---

### Post by lloyd_b on 2010-07-29
> **p.matulionis@gmail.com said:**
> I have a problem using command sudo make check:
```

root@paulius-laptop:/var/www/Xaira# sudo make check
Making check in indexer
make[1]: Entering directory `/var/www/Xaira/indexer'
make  test-indexer
make[2]: Entering directory `/var/www/Xaira/indexer'
make[2]: Nothing to be done for `test-indexer'.
make[2]: Leaving directory `/var/www/Xaira/indexer'
make  check-TESTS
make[2]: Entering directory `/var/www/Xaira/indexer'
/bin/bash: line 8: ./test-indexer: Permission denied
FAIL: test-indexer
==================
1 of 1 test failed
==================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/var/www/Xaira/indexer'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/var/www/Xaira/indexer'
make: *** [check-recursive] Error 1

```

Can anybody tell why I'm getting this error?

If looks like you have a file ("/var/www/Xaira/indexer/test-indexer") that does not have the "execute" bit set, so it's triggering a "Permission denied" when make tries to run it.

Since it appears to be ready to recreate the file, I'd try the following:```
mv /var/www/Xaira/indexer/test-indexer /var/www/Xaira/indexer/test-indexer.bak
``` and try running the command again - when it recreates the file, it should have proper permissions to be executable.

Lloyd B.

---

