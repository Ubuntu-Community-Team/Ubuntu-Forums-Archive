---
title: "Installing a program from source code (deluge)"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by super.rad on 2007-04-29
On the deluge website it says the latest build is available by checking the source code out of SVN

```
svn checkout http://deluge-torrent.org/svn/trunk deluge
```

could someone please tell me how i would download and install the program from the source code? thanks

---

### Post by luisromangz on 2007-04-29
Once you have downloaded the code using the command you wrote, I think, you should run
```
sudo python setup.py
```
and it should install.

Hope it works, I haven't tried because I use KTorrent.

---

### Post by zerobinary on 2007-04-29
i get error like this 
[HTML]code
./libtorrent/include/libtorrent/tracker_manager.hpp:217: error: invalid function declaration
./libtorrent/include/libtorrent/resource_request.hpp:75: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/resource_request.hpp:75: error: expected primary-expression before ‘int’
./libtorrent/include/libtorrent/resource_request.hpp:75: error: expected ‘;’ before ‘int’
./libtorrent/include/libtorrent/resource_request.hpp: In member function ‘int libtorrent::resource_request::left() const’:
./libtorrent/include/libtorrent/resource_request.hpp:71: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/resource_request.hpp:71: error: expected primary-expression before ‘int’
./libtorrent/include/libtorrent/resource_request.hpp:71: error: expected ‘;’ before ‘int’
./libtorrent/include/libtorrent/resource_request.hpp:71: error: expected unqualified-id before ‘>’ token
./libtorrent/include/libtorrent/torrent.hpp: At global scope:
./libtorrent/include/libtorrent/torrent.hpp:92: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/torrent.hpp:92: error: expected `{' before ‘enable_shared_from_this’
./libtorrent/include/libtorrent/torrent.hpp:92: error: expected initializer before ‘<’ token
./libtorrent/include/libtorrent/torrent.hpp:626: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/torrent.hpp:626: error: expected initializer before ‘torrent’
./libtorrent/include/libtorrent/torrent.hpp:631: error: invalid use of undefined type ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/piece_picker.hpp:58: error: forward declaration of ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/torrent.hpp: In member function ‘void libtorrent::torrent::force_tracker_request()’:
./libtorrent/include/libtorrent/torrent.hpp:633: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/torrent.hpp:634: error: ‘m_next_request’ was not declared in this scope
./libtorrent/include/libtorrent/torrent.hpp:634: error: ‘second_clock’ has not been declared
./libtorrent/include/libtorrent/torrent.hpp: At global scope:
./libtorrent/include/libtorrent/torrent.hpp:637: error: invalid use of undefined type ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/piece_picker.hpp:58: error: forward declaration of ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/torrent.hpp:637: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/torrent.hpp:645: error: invalid use of undefined type ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/piece_picker.hpp:58: error: forward declaration of ‘class libtorrent::torrent’
./libtorrent/include/libtorrent/torrent.hpp: In member function ‘void libtorrent::torrent::set_tracker_login(const std::string&, const std::string&)’:
./libtorrent/include/libtorrent/torrent.hpp:647: error: ‘m_username’ was not declared in this scope
./libtorrent/include/libtorrent/torrent.hpp:648: error: ‘m_password’ was not declared in this scope
./libtorrent/include/libtorrent/allocate_resources.hpp: At global scope:
./libtorrent/include/libtorrent/allocate_resources.hpp:61: error: ‘boost’ was not declared in this scope
./libtorrent/include/libtorrent/allocate_resources.hpp:61: error: template argument 2 is invalid
./libtorrent/include/libtorrent/allocate_resources.hpp:61: error: template argument 4 is invalid
./libtorrent/include/libtorrent/allocate_resources.hpp:61: error: expected ‘,’ or ‘...’ before ‘>’ token
./libtorrent/include/libtorrent/peer_connection.hpp:97: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/peer_connection.hpp:97: error: expected `{' before ‘noncopyable’
./libtorrent/include/libtorrent/peer_connection.hpp:97: error: invalid function declaration
./libtorrent/include/libtorrent/hasher.hpp:45: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/hasher.hpp:45: error: ISO C++ forbids declaration of ‘uint32_t’ with no type
./libtorrent/include/libtorrent/hasher.hpp:45: error: expected ‘;’ before ‘state’
./libtorrent/include/libtorrent/hasher.hpp:46: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/hasher.hpp:46: error: ISO C++ forbids declaration of ‘uint32_t’ with no type
./libtorrent/include/libtorrent/hasher.hpp:46: error: expected ‘;’ before ‘count’
./libtorrent/include/libtorrent/hasher.hpp:47: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/hasher.hpp:47: error: ISO C++ forbids declaration of ‘uint8_t’ with no type
./libtorrent/include/libtorrent/hasher.hpp:47: error: expected ‘;’ before ‘buffer’
./libtorrent/include/libtorrent/hasher.hpp:51: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/hasher.hpp:51: error: expected ‘,’ or ‘...’ before ‘const’
./libtorrent/include/libtorrent/hasher.hpp:52: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/hasher.hpp:52: error: expected ‘,’ or ‘...’ before ‘*’ token
./libtorrent/include/libtorrent/hasher.hpp: In constructor ‘libtorrent::hasher::hasher(const char*, int)’:
./libtorrent/include/libtorrent/hasher.hpp:93: error: invalid conversion from ‘const unsigned char*’ to ‘int’
./libtorrent/include/libtorrent/hasher.hpp:51: error: too many arguments to function ‘void SHA1Update(SHA1_CTX*, int)’
./libtorrent/include/libtorrent/hasher.hpp:93: error: at this point in file
./libtorrent/include/libtorrent/hasher.hpp: In member function ‘void libtorrent::hasher::update(const char*, int)’:
./libtorrent/include/libtorrent/hasher.hpp:99: error: invalid conversion from ‘const unsigned char*’ to ‘int’
./libtorrent/include/libtorrent/hasher.hpp:51: error: too many arguments to function ‘void SHA1Update(SHA1_CTX*, int)’
./libtorrent/include/libtorrent/hasher.hpp:99: error: at this point in file
./libtorrent/include/libtorrent/hasher.hpp: In member function ‘libtorrent::sha1_hash libtorrent::hasher::final()’:
./libtorrent/include/libtorrent/hasher.hpp:105: error: invalid conversion from ‘unsigned char*’ to ‘int’
./libtorrent/include/libtorrent/hasher.hpp:105: error:   initializing argument 2 of ‘void SHA1Final(SHA1_CTX*, int)’
./libtorrent/include/libtorrent/ip_filter.hpp: In member function ‘void libtorrent::detail::filter_impl<Addr>::add_rule(Addr, Addr, int)’:
./libtorrent/include/libtorrent/ip_filter.hpp:92: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/ip_filter.hpp:93: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/ip_filter.hpp: At global scope:
./libtorrent/include/libtorrent/ip_filter.hpp:260: error: ‘boost’ has not been declared
./libtorrent/include/libtorrent/ip_filter.hpp:260: error: ISO C++ forbids declaration of ‘tuple’ with no type
./libtorrent/include/libtorrent/ip_filter.hpp:260: error: typedef name may not be a nested-name-specifier
./libtorrent/include/libtorrent/ip_filter.hpp:260: error: expected ‘;’ before ‘<’ token
./libtorrent/include/libtorrent/ip_filter.hpp:263: error: ‘filter_tuple_t’ does not name a type
src/deluge_core.cpp:168: error: ‘boost’ has not been declared
src/deluge_core.cpp:168: error: expected ‘,’ or ‘...’ before ‘const’
src/deluge_core.cpp: In function ‘long int internal_add_torrent(const std::string&, float, bool, int)’:
src/deluge_core.cpp:173: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:173: error: expected primary-expression before ‘char’
src/deluge_core.cpp:173: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:173: error: expected primary-expression before ‘char’
src/deluge_core.cpp:182: error: ‘boost’ has not been declared
src/deluge_core.cpp:182: error: expected `;' before ‘resumeFile’
src/deluge_core.cpp:183: error: ‘resumeFile’ was not declared in this scope
src/deluge_core.cpp:184: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:184: error: expected primary-expression before ‘char’
src/deluge_core.cpp:185: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:185: error: expected primary-expression before ‘char’
src/deluge_core.cpp:187: error: expected type-specifier before ‘boost’
src/deluge_core.cpp:187: error: expected `)' before ‘::’ token
src/deluge_core.cpp:187: error: expected `{' before ‘::’ token
src/deluge_core.cpp:187: error: ‘::filesystem’ has not been declared
src/deluge_core.cpp:187: error: expected primary-expression before ‘)’ token
src/deluge_core.cpp:187: error: expected `;' before ‘)’ token
src/deluge_core.cpp:193: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:193: error: ‘save_path’ was not declared in this scope
src/deluge_core.cpp: In function ‘void internal_remove_torrent(long int)’:
src/deluge_core.cpp:214: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: At global scope:
src/deluge_core.cpp:233: error: ‘boost’ has not been declared
src/deluge_core.cpp:233: error: expected ‘,’ or ‘...’ before ‘const’
src/deluge_core.cpp: In function ‘void internal_add_files(libtorrent::torrent_info&, int)’:
src/deluge_core.cpp:236: error: ‘boost’ has not been declared
src/deluge_core.cpp:236: error: expected `;' before ‘f’
src/deluge_core.cpp:237: error: ‘f’ was not declared in this scope
src/deluge_core.cpp:237: error: ‘is_directory’ was not declared in this scope
src/deluge_core.cpp:239: error: ‘boost’ has not been declared
src/deluge_core.cpp:239: error: expected `;' before ‘i’
src/deluge_core.cpp:239: error: ‘i’ was not declared in this scope
src/deluge_core.cpp:239: error: ‘end’ was not declared in this scope
src/deluge_core.cpp:240: error: ‘p’ was not declared in this scope
src/deluge_core.cpp:240: error: ‘l’ was not declared in this scope
src/deluge_core.cpp:242: error: ‘l’ was not declared in this scope
src/deluge_core.cpp:242: error: ‘file_size’ was not declared in this scope
src/deluge_core.cpp: In function ‘PyObject* torrent_init(PyObject*, PyObject*)’:
src/deluge_core.cpp:289: error: ‘boost’ has not been declared
src/deluge_core.cpp:298: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:307: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:308: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:309: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:311: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:312: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_quit(PyObject*, PyObject*)’:
src/deluge_core.cpp:340: warning: possible problem detected in invocation of delete operator:
src/deluge_core.cpp:104: warning: ‘M_ses’ has incomplete type
./libtorrent/include/libtorrent/session.hpp:111: warning: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:340: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
src/deluge_core.cpp: In function ‘PyObject* torrent_save_fastresume(PyObject*, PyObject*)’:
src/deluge_core.cpp:375: error: ‘boost’ has not been declared
src/deluge_core.cpp:375: error: expected `;' before ‘out’
src/deluge_core.cpp:377: error: ‘out’ was not declared in this scope
src/deluge_core.cpp:379: error: ‘ostream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:379: error: expected primary-expression before ‘char’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_max_half_open(PyObject*, PyObject*)’:
src/deluge_core.cpp:394: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_download_rate_limit(PyObject*, PyObject*)’:
src/deluge_core.cpp:406: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_upload_rate_limit(PyObject*, PyObject*)’:
src/deluge_core.cpp:418: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_listen_on(PyObject*, PyObject*)’:
src/deluge_core.cpp:429: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_is_listening(PyObject*, PyObject*)’:
src/deluge_core.cpp:437: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_listening_port(PyObject*, PyObject*)’:
src/deluge_core.cpp:444: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_max_uploads(PyObject*, PyObject*)’:
src/deluge_core.cpp:453: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_set_max_connections(PyObject*, PyObject*)’:
src/deluge_core.cpp:465: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_add_torrent(PyObject*, PyObject*)’:
src/deluge_core.cpp:477: error: ‘boost’ has not been declared
src/deluge_core.cpp:477: error: expected `;' before ‘save_dir_2’
src/deluge_core.cpp:481: error: ‘save_dir_2’ was not declared in this scope
src/deluge_core.cpp:491: error: expected type-specifier before ‘boost’
src/deluge_core.cpp:491: error: expected `)' before ‘::’ token
src/deluge_core.cpp:491: error: expected `{' before ‘::’ token
src/deluge_core.cpp:491: error: ‘::filesystem’ has not been declared
src/deluge_core.cpp:491: error: expected primary-expression before ‘)’ token
src/deluge_core.cpp:491: error: expected `;' before ‘)’ token
src/deluge_core.cpp:493: error: expected primary-expression before ‘catch’
src/deluge_core.cpp:493: error: expected `;' before ‘catch’
src/deluge_core.cpp: In function ‘PyObject* torrent_get_torrent_state(PyObject*, PyObject*)’:
src/deluge_core.cpp:596: error: ‘struct libtorrent::torrent_status’ has no member named ‘total_download’
src/deluge_core.cpp:598: error: ‘struct libtorrent::torrent_status’ has no member named ‘total_upload’
src/deluge_core.cpp:601: error: ‘boost’ has not been declared
src/deluge_core.cpp:601: error: ‘struct libtorrent::torrent_status’ has no member named ‘next_announce’
src/deluge_core.cpp:604: error: ‘struct libtorrent::torrent_status’ has no member named ‘total_done’
src/deluge_core.cpp:608: error: ‘const class libtorrent::torrent_info’ has no member named ‘total_size’
src/deluge_core.cpp:609: error: ‘const class libtorrent::torrent_info’ has no member named ‘piece_length’
src/deluge_core.cpp:615: error: ‘struct libtorrent::torrent_status’ has no member named ‘total_wanted’
src/deluge_core.cpp:616: error: ‘struct libtorrent::torrent_status’ has no member named ‘total_wanted_done’
src/deluge_core.cpp: In function ‘PyObject* torrent_pop_event(PyObject*, PyObject*)’:
src/deluge_core.cpp:625: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_get_session_info(PyObject*, PyObject*)’:
src/deluge_core.cpp:796: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_get_peer_info(PyObject*, PyObject*)’:
src/deluge_core.cpp:843: error: ‘struct libtorrent::peer_info’ has no member named ‘total_download’
src/deluge_core.cpp:845: error: ‘struct libtorrent::peer_info’ has no member named ‘total_upload’
src/deluge_core.cpp: In function ‘PyObject* torrent_get_file_info(PyObject*, PyObject*)’:
src/deluge_core.cpp:905: error: ‘const struct libtorrent::file_entry’ has no member named ‘path’
src/deluge_core.cpp:906: error: ‘const struct libtorrent::file_entry’ has no member named ‘offset’
src/deluge_core.cpp:907: error: ‘const struct libtorrent::file_entry’ has no member named ‘size’
src/deluge_core.cpp: In function ‘PyObject* torrent_start_DHT(PyObject*, PyObject*)’:
src/deluge_core.cpp:981: error: ‘boost’ has not been declared
src/deluge_core.cpp:981: error: expected `;' before ‘tempPath’
src/deluge_core.cpp:982: error: ‘boost’ has not been declared
src/deluge_core.cpp:982: error: expected `;' before ‘DHT_state_file’
src/deluge_core.cpp:983: error: ‘DHT_state_file’ was not declared in this scope
src/deluge_core.cpp:987: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:987: error: expected primary-expression before ‘char’
src/deluge_core.cpp:988: error: ‘istream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:988: error: expected primary-expression before ‘char’
src/deluge_core.cpp:989: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:997: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:1000: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:1002: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:1004: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_stop_DHT(PyObject*, PyObject*)’:
src/deluge_core.cpp:1018: error: ‘boost’ has not been declared
src/deluge_core.cpp:1018: error: expected `;' before ‘tempPath’
src/deluge_core.cpp:1021: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp:1025: error: ‘boost’ has not been declared
src/deluge_core.cpp:1025: error: expected `;' before ‘out’
src/deluge_core.cpp:1026: error: ‘out’ was not declared in this scope
src/deluge_core.cpp:1027: error: ‘ostream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:1027: error: expected primary-expression before ‘char’
src/deluge_core.cpp: In function ‘PyObject* torrent_get_DHT_info(PyObject*, PyObject*)’:
src/deluge_core.cpp:1038: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
src/deluge_core.cpp: In function ‘PyObject* torrent_create_torrent(PyObject*, PyObject*)’:
src/deluge_core.cpp:1083: error: ‘boost’ has not been declared
src/deluge_core.cpp:1083: error: expected `;' before ‘full_path’
src/deluge_core.cpp:1084: error: ‘boost’ has not been declared
src/deluge_core.cpp:1084: error: expected `;' before ‘out’
src/deluge_core.cpp:1087: error: ‘full_path’ was not declared in this scope
src/deluge_core.cpp:1109: error: ‘class libtorrent::storage’ has no member named ‘read’
src/deluge_core.cpp:1109: error: ‘class libtorrent::torrent_info’ has no member named ‘piece_size’
src/deluge_core.cpp:1110: error: ‘class libtorrent::torrent_info’ has no member named ‘piece_size’
src/deluge_core.cpp:1118: error: ‘ostream_iterator’ is not a member of ‘std’
src/deluge_core.cpp:1118: error: expected primary-expression before ‘char’
src/deluge_core.cpp: In function ‘PyObject* torrent_apply_IP_filter(PyObject*, PyObject*)’:
src/deluge_core.cpp:1162: error: invalid use of undefined type ‘class libtorrent::session’
./libtorrent/include/libtorrent/session.hpp:111: error: forward declaration of ‘class libtorrent::session’
./libtorrent/include/libtorrent/asio/ip/basic_endpoint.hpp: In member function ‘asio::ip::address asio::ip::basic_endpoint<Protocol>::address() const [with Protocol = asio::ip::tcp]’:
src/deluge_core.cpp:650:   instantiated from here
./libtorrent/include/libtorrent/asio/ip/basic_endpoint.hpp:262: error: call of overloaded ‘address_v4(asio::detail::u_long_type)’ is ambiguous
./libtorrent/include/libtorrent/asio/ip/address_v4.hpp:63: note: candidates are: asio::ip::address_v4::address_v4(long unsigned int)
./libtorrent/include/libtorrent/asio/ip/address_v4.hpp:56: note:                 asio::ip::address_v4::address_v4(int)
./libtorrent/include/libtorrent/ip_filter.hpp: In constructor ‘libtorrent::detail::filter_impl<Addr>::filter_impl() [with Addr = asio::ip::address_v4]’:
./libtorrent/include/libtorrent/ip_filter.hpp:247:   instantiated from here
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v4’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v4’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v4’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v4’
./libtorrent/include/libtorrent/ip_filter.hpp: In constructor ‘libtorrent::detail::filter_impl<Addr>::filter_impl() [with Addr = asio::ip::address_v6]’:
./libtorrent/include/libtorrent/ip_filter.hpp:247:   instantiated from here
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v6’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v6’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v6’
./libtorrent/include/libtorrent/ip_filter.hpp:84: error: no type named ‘bytes_type’ in ‘class asio::ip::address_v6’
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp: In member function ‘typename std::list<std::pair<const _Key, _Tp>, std::allocator<std::pair<const _Key, _Tp> > >::iterator asio::detail::hash_map<K, V>::find(const K&) [with K = int, V = asio::detail::reactor_op_queue<int>::op_base*]’:
./libtorrent/include/libtorrent/asio/detail/reactor_op_queue.hpp:142:   instantiated from ‘void asio::detail::reactor_op_queue<Descriptor>::dispatch_all_operations(Descriptor, int) [with Descriptor = int]’
./libtorrent/include/libtorrent/asio/detail/epoll_reactor.hpp:386:   instantiated from ‘void asio::detail::epoll_reactor<Own_Thread>::run(bool) [with bool Own_Thread = false]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:241:   instantiated from ‘size_t asio::detail::task_io_service<Task>::do_one(asio::detail::scoped_lock<asio::detail::null_mutex>&, asio::detail::task_io_service<Task>::idle_thread_info*) [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:83:   instantiated from ‘size_t asio::detail::task_io_service<Task>::run() [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/impl/io_service.ipp:36:   instantiated from here
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp:89: error: ‘hash_value’ was not declared in this scope
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp: In member function ‘void asio::detail::hash_map<K, V>::erase(typename std::list<std::pair<const _Key, _Tp>, std::allocator<std::pair<const _Key, _Tp> > >::iterator) [with K = int, V = asio::detail::reactor_op_queue<int>::op_base*]’:
./libtorrent/include/libtorrent/asio/detail/reactor_op_queue.hpp:161:   instantiated from ‘void asio::detail::reactor_op_queue<Descriptor>::dispatch_all_operations(Descriptor, int) [with Descriptor = int]’
./libtorrent/include/libtorrent/asio/detail/epoll_reactor.hpp:386:   instantiated from ‘void asio::detail::epoll_reactor<Own_Thread>::run(bool) [with bool Own_Thread = false]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:241:   instantiated from ‘size_t asio::detail::task_io_service<Task>::do_one(asio::detail::scoped_lock<asio::detail::null_mutex>&, asio::detail::task_io_service<Task>::idle_thread_info*) [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:83:   instantiated from ‘size_t asio::detail::task_io_service<Task>::run() [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/impl/io_service.ipp:36:   instantiated from here
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp:150: error: ‘hash_value’ was not declared in this scope
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp: In member function ‘typename std::list<std::pair<const _Key, _Tp>, std::allocator<std::pair<const _Key, _Tp> > >::const_iterator asio::detail::hash_map<K, V>::find(const K&) const [with K = int, V = asio::detail::reactor_op_queue<int>::op_base*]’:
./libtorrent/include/libtorrent/asio/detail/reactor_op_queue.hpp:98:   instantiated from ‘bool asio::detail::reactor_op_queue<Descriptor>::has_operation(Descriptor) const [with Descriptor = int]’
./libtorrent/include/libtorrent/asio/detail/epoll_reactor.hpp:406:   instantiated from ‘void asio::detail::epoll_reactor<Own_Thread>::run(bool) [with bool Own_Thread = false]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:241:   instantiated from ‘size_t asio::detail::task_io_service<Task>::do_one(asio::detail::scoped_lock<asio::detail::null_mutex>&, asio::detail::task_io_service<Task>::idle_thread_info*) [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/detail/task_io_service.hpp:83:   instantiated from ‘size_t asio::detail::task_io_service<Task>::run() [with Task = asio::detail::epoll_reactor<false>]’
./libtorrent/include/libtorrent/asio/impl/io_service.ipp:36:   instantiated from here
./libtorrent/include/libtorrent/asio/detail/hash_map.hpp:107: error: ‘hash_value’ was not declared in this scope
error: command 'gcc' failed with exit status 1
[/HTML]

---

### Post by super.rad on 2007-04-29
thanks luisromangz  it worked perfectly, but i ended up using utorrent through wine anyway

---

### Post by zerobinary on 2007-05-01
python: can't open file 'setup.py': [Errno 2] No such file or directory

---

### Post by kelvin spratt on 2007-05-01
you can download dleluge from get deb web site its a deb file you need gdeb installer from add remove programs instal by double clicking easyer than windows

---

