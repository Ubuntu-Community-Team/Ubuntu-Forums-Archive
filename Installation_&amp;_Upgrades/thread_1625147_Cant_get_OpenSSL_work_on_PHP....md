---
title: "Cant get OpenSSL work on PHP..."
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by mario.martinez on 2010-11-18
im using: Ubuntu 10.04.1 LTS

i have a webserver with apache and i want to open, and use some .key.pem

Ill try in windows and works fine..

$file="C:\AppServ\www\pfsr\certificados\IRT0406122F1_33.key.pem";
$pkeyid = openssl_get_privatekey(file_get_contents($file));

openssl_sign($cadena, $crypttext, $pkeyid, OPENSSL_ALGO_MD5);
openssl_free_key($pkeyid);
$sello = base64_encode($crypttext); 
echo $sello;

$pkeyid is Empty, 
i can use openssl in the command line, but not in PHP

---

