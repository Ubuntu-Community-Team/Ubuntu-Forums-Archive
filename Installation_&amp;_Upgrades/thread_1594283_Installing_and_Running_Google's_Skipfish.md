---
title: "Installing and Running Google's Skipfish?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by minervauk on 2010-10-12
Hi all - 

I am quite new to Linux and already quite frustrated being unable to run few things which should be fairly easy. 

I have been trying to run - Skipfish- the security reconnaissance tool from Google. ( [http://code.google.com/p/skipfish/](http://code.google.com/p/skipfish/) ) 

It seems it is very easy to use after searching (actually quite a lot) 

I have installed whatever they asked for it but not sure what I am missing i.e.

Zlib
openssl
libidn 

etc 

[B]Codes I am using on terminal: 

[/B]I have tried lots of different codes - the last one is : 

wget [http://skipfish.googlecode.com/files/skipfish-1.69b.tgz]("http://skipfish.googlecode.com/files/skipfish-1.01b.tgz")
tar zxvf skipfish-1.69b.tgz
cd skipfish-1.69b
make

**** at this point I get this message**s:



cc -L/usr/local/lib/ -L/opt/local/lib skipfish.c -o skipfish -O3 -Wno-format -Wall -funsigned-char -g -ggdb -I/usr/local/include/ -I/opt/local/include/  -D_FORTIFY_SOURCE=0 -DVERSION=\"1.69b\" \
          http_client.c database.c crawler.c analysis.c report.c -lcrypto -lssl -lidn -lz
In file included from crawler.h:26,
                 from skipfish.c:41:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from crawler.h:26,
                 from skipfish.c:41:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
skipfish.c: In function ‘main’:
skipfish.c:208: warning: implicit declaration of function ‘SSL_library_init’
skipfish.c:582: warning: implicit declaration of function ‘EVP_cleanup’
skipfish.c:583: warning: implicit declaration of function ‘CRYPTO_cleanup_all_ex_data’
http_client.c:37:25: error: openssl/ssl.h: No such file or directory
http_client.c:38:25: error: openssl/err.h: No such file or directory
In file included from database.h:29,
                 from http_client.c:45:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
http_client.c: In function ‘destroy_unlink_conn’:
http_client.c:1646: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1646: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1649: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1649: warning: implicit declaration of function ‘SSL_free’
http_client.c:1649: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1650: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1650: warning: implicit declaration of function ‘SSL_CTX_free’
http_client.c:1650: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1651: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1652: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c: In function ‘reuse_conn’:
http_client.c:1662: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1662: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1663: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1664: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:1665: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1666: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:1666: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1668: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:1668: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c: In function ‘check_ssl’:
http_client.c:1773: error: ‘X509’ undeclared (first use in this function)
http_client.c:1773: error: (Each undeclared identifier is reported only once
http_client.c:1773: error: for each function it appears in.)
http_client.c:1773: error: ‘p’ undeclared (first use in this function)
http_client.c:1775: warning: implicit declaration of function ‘SSL_get_peer_certificate’
http_client.c:1775: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1783: warning: implicit declaration of function ‘ASN1_UTCTIME_cmp_time_t’
http_client.c:1787: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1788: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1792: warning: implicit declaration of function ‘X509_NAME_oneline’
http_client.c:1794: warning: left-hand operand of comma expression has no effect
http_client.c:1794: warning: left-hand operand of comma expression has no effect
http_client.c:1795: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1796: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1798: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1799: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1806: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1818: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1819: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1821: warning: implicit declaration of function ‘X509_free’
http_client.c:1823: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1824: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1826: error: ‘struct conn_entry’ has no member named ‘ssl_checked’
http_client.c: In function ‘conn_associate’:
http_client.c:1881: error: ‘errno’ undeclared (first use in this function)
http_client.c:1881: error: ‘EINPROGRESS’ undeclared (first use in this function)
http_client.c:1887: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1887: warning: implicit declaration of function ‘SSL_CTX_new’
http_client.c:1887: warning: implicit declaration of function ‘SSLv23_client_method’
http_client.c:1889: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1891: warning: implicit declaration of function ‘SSL_CTX_set_mode’
http_client.c:1891: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1891: error: ‘SSL_MODE_ENABLE_PARTIAL_WRITE’ undeclared (first use in this function)
http_client.c:1892: error: ‘SSL_MODE_ACCEPT_MOVING_WRITE_BUFFER’ undeclared (first use in this function)
http_client.c:1894: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1894: warning: implicit declaration of function ‘SSL_new’
http_client.c:1894: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1896: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1897: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1901: warning: implicit declaration of function ‘SSL_set_fd’
http_client.c:1901: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1902: warning: implicit declaration of function ‘SSL_set_connect_state’
http_client.c:1902: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1908: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1910: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1910: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1916: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1921: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1922: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1922: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c: In function ‘next_from_queue’:
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:1954: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1964: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1984: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1985: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1986: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1987: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1991: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1994: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2000: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2001: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2006: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2024: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2025: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2027: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2038: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2041: warning: implicit declaration of function ‘SSL_read’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2047: warning: implicit declaration of function ‘SSL_get_error’
http_client.c:2047: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2048: error: ‘SSL_ERROR_WANT_WRITE’ undeclared (first use in this function)
http_client.c:2048: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2049: error: ‘SSL_ERROR_WANT_READ’ undeclared (first use in this function)
http_client.c:2054: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2054: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2060: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2066: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2068: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2068: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2076: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2082: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2089: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2096: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2102: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2113: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2114: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2116: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2116: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2122: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2124: warning: implicit declaration of function ‘SSL_write’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2125: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2125: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2130: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2131: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2134: error: ‘struct conn_entry’ has no member named ‘ssl_checked’
http_client.c:2137: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:2137: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2138: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2138: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2144: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2146: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2163: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2165: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2166: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2168: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2169: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2209: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:2213: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c: In function ‘http_req_list’:
http_client.c:2520: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2521: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2534: error: ‘struct conn_entry’ has no member named ‘next’
In file included from database.c:33:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from database.c:33:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
In file included from crawler.c:30:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from crawler.c:30:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
In file included from analysis.c:28:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from analysis.c:28:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
analysis.c: In function ‘maybe_xsrf’:
analysis.c:398: warning: implicit declaration of function ‘time’
In file included from report.c:33:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from report.c:33:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
make: *** [skipfish] Error 1
john@john-laptop:~/skipfish-1.69b$ sudo make
cc -L/usr/local/lib/ -L/opt/local/lib skipfish.c -o skipfish -O3 -Wno-format -Wall -funsigned-char -g -ggdb -I/usr/local/include/ -I/opt/local/include/  -D_FORTIFY_SOURCE=0 -DVERSION=\"1.69b\" \
          http_client.c database.c crawler.c analysis.c report.c -lcrypto -lssl -lidn -lz
In file included from crawler.h:26,
                 from skipfish.c:41:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from crawler.h:26,
                 from skipfish.c:41:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
skipfish.c: In function ‘main’:
skipfish.c:208: warning: implicit declaration of function ‘SSL_library_init’
skipfish.c:582: warning: implicit declaration of function ‘EVP_cleanup’
skipfish.c:583: warning: implicit declaration of function ‘CRYPTO_cleanup_all_ex_data’
http_client.c:37:25: error: openssl/ssl.h: No such file or directory
http_client.c:38:25: error: openssl/err.h: No such file or directory
In file included from database.h:29,
                 from http_client.c:45:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
http_client.c: In function ‘destroy_unlink_conn’:
http_client.c:1646: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1646: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1647: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1648: error: ‘struct conn_entry’ has no member named ‘prev’
http_client.c:1649: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1649: warning: implicit declaration of function ‘SSL_free’
http_client.c:1649: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1650: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1650: warning: implicit declaration of function ‘SSL_CTX_free’
http_client.c:1650: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1651: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1652: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c: In function ‘reuse_conn’:
http_client.c:1662: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1662: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1663: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1664: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:1665: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1666: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:1666: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1667: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1668: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:1668: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c: In function ‘check_ssl’:
http_client.c:1773: error: ‘X509’ undeclared (first use in this function)
http_client.c:1773: error: (Each undeclared identifier is reported only once
http_client.c:1773: error: for each function it appears in.)
http_client.c:1773: error: ‘p’ undeclared (first use in this function)
http_client.c:1775: warning: implicit declaration of function ‘SSL_get_peer_certificate’
http_client.c:1775: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1783: warning: implicit declaration of function ‘ASN1_UTCTIME_cmp_time_t’
http_client.c:1787: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1788: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1792: warning: implicit declaration of function ‘X509_NAME_oneline’
http_client.c:1794: warning: left-hand operand of comma expression has no effect
http_client.c:1794: warning: left-hand operand of comma expression has no effect
http_client.c:1795: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1796: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1798: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1799: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1806: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1818: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1819: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1821: warning: implicit declaration of function ‘X509_free’
http_client.c:1823: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1824: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1826: error: ‘struct conn_entry’ has no member named ‘ssl_checked’
http_client.c: In function ‘conn_associate’:
http_client.c:1881: error: ‘errno’ undeclared (first use in this function)
http_client.c:1881: error: ‘EINPROGRESS’ undeclared (first use in this function)
http_client.c:1887: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1887: warning: implicit declaration of function ‘SSL_CTX_new’
http_client.c:1887: warning: implicit declaration of function ‘SSLv23_client_method’
http_client.c:1889: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1891: warning: implicit declaration of function ‘SSL_CTX_set_mode’
http_client.c:1891: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1891: error: ‘SSL_MODE_ENABLE_PARTIAL_WRITE’ undeclared (first use in this function)
http_client.c:1892: error: ‘SSL_MODE_ACCEPT_MOVING_WRITE_BUFFER’ undeclared (first use in this function)
http_client.c:1894: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1894: warning: implicit declaration of function ‘SSL_new’
http_client.c:1894: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1896: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1897: error: ‘struct conn_entry’ has no member named ‘srv_ctx’
http_client.c:1901: warning: implicit declaration of function ‘SSL_set_fd’
http_client.c:1901: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1902: warning: implicit declaration of function ‘SSL_set_connect_state’
http_client.c:1902: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:1908: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1910: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1910: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1916: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1921: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:1922: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1922: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c: In function ‘next_from_queue’:
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1951: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:1954: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1964: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1982: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1984: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1985: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1986: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1987: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1991: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:1993: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:1994: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1995: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:1999: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2000: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2001: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2002: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2006: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2007: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2024: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2025: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2027: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2033: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2038: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2041: warning: implicit declaration of function ‘SSL_read’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2041: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2047: warning: implicit declaration of function ‘SSL_get_error’
http_client.c:2047: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2048: error: ‘SSL_ERROR_WANT_WRITE’ undeclared (first use in this function)
http_client.c:2048: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2049: error: ‘SSL_ERROR_WANT_READ’ undeclared (first use in this function)
http_client.c:2054: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2054: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2060: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2061: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2066: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2068: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2068: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘read_buf’
http_client.c:2075: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2076: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2082: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2083: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2089: error: ‘struct conn_entry’ has no member named ‘read_len’
http_client.c:2096: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2097: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2102: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2113: error: ‘struct conn_entry’ has no member named ‘SSL_rd_w_wr’
http_client.c:2114: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2116: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2116: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2122: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2124: warning: implicit declaration of function ‘SSL_write’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:2124: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2125: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2125: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2130: error: ‘struct conn_entry’ has no member named ‘srv_ssl’
http_client.c:2131: error: ‘struct conn_entry’ has no member named ‘SSL_wr_w_rd’
http_client.c:2134: error: ‘struct conn_entry’ has no member named ‘ssl_checked’
http_client.c:2137: error: ‘struct conn_entry’ has no member named ‘write_buf’
http_client.c:2137: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2138: error: ‘struct conn_entry’ has no member named ‘write_len’
http_client.c:2138: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2144: error: ‘struct conn_entry’ has no member named ‘write_off’
http_client.c:2146: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2163: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2165: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2166: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2168: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2169: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2170: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2209: error: ‘struct conn_entry’ has no member named ‘next’
http_client.c:2213: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c: In function ‘http_req_list’:
http_client.c:2520: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2521: error: ‘struct conn_entry’ has no member named ‘q’
http_client.c:2534: error: ‘struct conn_entry’ has no member named ‘next’
In file included from database.c:33:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from database.c:33:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
In file included from crawler.c:30:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from crawler.c:30:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
In file included from analysis.c:28:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from analysis.c:28:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
analysis.c: In function ‘maybe_xsrf’:
analysis.c:398: warning: implicit declaration of function ‘time’
In file included from report.c:33:
http_client.h:26:25: error: openssl/ssl.h: No such file or directory
In file included from report.c:33:
http_client.h:189: error: expected specifier-qualifier-list before ‘SSL_CTX’
make: *** [skipfish] Error 1
 

-----------------------------------------


No Idea what I am doing wrong. 

Any input would be much appreciated

Thanks

---

### Post by mikechant on 2010-10-12
Try installing the dependancies first with

```
sudo apt-get install libssl-dev zlib1g-dev libidn11
```

Then navigate to the skipfish directory and run 'make' as before.

If this doesn't work, try following the complete instructions at:

[http://digitivity.org/943/how-to-install-google-skipfish-on-ubuntu-linux](http://digitivity.org/943/how-to-install-google-skipfish-on-ubuntu-linux)

Don't worry about any messages apt-get gives about requested packages already being installed (can't remember if it does this).

---

### Post by minervauk on 2010-10-12
Oh brilliant! Thanks Mike! It's working like a chum! :) 

Although I already had libssl-dev zlib1g-dev libidn11 etc but I done them again. 

Here is the post I am going to copy paste from [http://digitivity.org/943/how-to-install-google-skipfish-on-ubuntu-linux](http://digitivity.org/943/how-to-install-google-skipfish-on-ubuntu-linux) 

just in case if they delete  their blog or something - 

The first three are installed by default on Ubuntu. In case they&#8217;re not install them with this command in a terminal:

```
sudo apt-get install gcc make libc6 libc6-dev
```

To install the last three requirements, enter this command:

```
sudo apt-get install libssl-dev zlib1g-dev libidn11
```

[SIZE="4"]**Building Skipfish**[/SIZE]

[SIZE="3"]**Download Skipfish**[/SIZE]

Download the latest version of Skipfish from here:

[http://code.google.com/p/skipfish/downloads/list](http://code.google.com/p/skipfish/downloads/list)

The current version (as of this writing) was 1.69b [LINK].

Save the file someplace, and then either right-click on it in the file manager and choose &#8220;Extract here&#8220;.

Or go to the directory where you saved it and enter this:

```
tar xzf skipfish-1.69b.tgz
```

**Setting Paths**

You may or may not need this step, but this will set the paths for header files and library files:

```
export CFLAGS="-I/usr/include/"
export LDFLAGS="-L/usr/lib/ssl/engines -L/usr/lib/ -L/usr/lib/ssl/"
```

**Compiling Skipfish**

Next, compile Skipfish. Enter the directory that was extracted earlier, and use &#8220;make&#8221; to start the build process:

```
cd skipfish-1.69b
nice make
```

Note: nice prevents make from monopolizing your system&#8217;s CPU.
Here&#8217;s the result:

```
cc -L/usr/lib/ssl/engines -L/usr/lib/ -L/usr/lib/ssl/ -L/usr/local/lib/ -L/opt/local/lib skipfish.c -o skipfish -O3 -Wno-format -Wall -funsigned-char -g -ggdb -I/usr/local/include/ -I/opt/local/include/ -I/usr/include/ -D_FORTIFY_SOURCE=0 \
	      http_client.c database.c crawler.c analysis.c report.c -lcrypto -lssl -lidn -lz
```
 
See dictionaries/README-FIRST to pick a dictionary for the tool.
 
Having problems with your scans? Be sure to visit:

[http://code.google.com/p/skipfish/wiki/KnownIssues](http://code.google.com/p/skipfish/wiki/KnownIssues)

After you do this, there should be an executable file named &#8220;skipfish&#8221; in the current directory. If not, or if there was an error, you probably are missing a requirement or a path is incorrectly specified.

**Using Skipfish**

This is just a basic introduction.

In the &#8220;skipfish&#8221; directory, enter these commands:

```
touch dictionaries/empty.wl
ln -s dictionaries/empty.wl skipfish.wl
mkdir ../out
./skipfish -o ../out/ [http://example.com](http://example.com)

```

This creates a blank wordlist file, and an output directory, and then launches Skipfish to scan the specified webserver. (Replace example.com with your webserver address. Make sure you have permission to scan that address.)
Hit Ctrl+c to stop the scan.

Then view the result with Firefox (not Safari or Chrome):

```
firefox ../out/index.html
``` 

Hope the next person with the same problem will find this post helpful.

---

