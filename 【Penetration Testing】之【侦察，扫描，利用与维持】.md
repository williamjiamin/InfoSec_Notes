# 【Penetration Testing】

同样的工具，在不同的人手里，是不同的



结构化的知识体系（有章法）

# 1.侦察！！！千万不要冲动！！！：公开信息

## 1）用的是什么技术，什么架构，各个结构之间的关系）*为了避免“看似是漏洞，但是实际上是坑，圈套的设计”

## 2) IP地址（站长之家，whois，阿里云，华为云，Amazon），domains，subdomain。，DNS服务器

shop.lexueoude.com



## 3）搜索引擎（site: baidu.com 搜索类似站点筛选，https://archive.org/ ，google，Bing，类似快照功能）



## 4) 善用社交网络、公开信息。



### 4.1.搜索引擎（主要是PC时代的-适用博客、贸易网站、展示型网站）：google、baidu、bing、duckduckgo



### 4.2 社交网络（主要是后PC时代或者移动互联网时代的信息来源）：LinkedIn（从业经历、技能与获取时间、相关人脉等），Facebook, Instangram.



### 4.3 公共信息与舆论平台：大趋势，事实信息获取与探讨



### 4.4 功能性App：利用绑定、实名制、转账等功能（还可以利用低等级信息综合组合与推断获取高等级信息内容）





### 建议：1.主动侦查 （直接与应用进行交互/url）2.被动侦查（尽量完全不与测试/渗透应用有任何的网络packets交换）------->三方cache信息(快照snapshot)



# 2.黑盒渗透测试（Black Box Pen-Testing）



## 2.1 DNS可以进行更改（互联网基础设施）

## 2.2 DNS可以作为信息获取的重要来源（whois提取信息）

## 2.3 拿到DNS server信息后继续dig，找到所有（尽可能越多越好的）相关联主机

## 2.4 dig与zone transfer信息暴露风险

## 案例：使用测试网站
```
dig axfr @nsztm1.digi.ninja zonetransfer.me
```

```
william@172:~$ dig axfr @nsztm1.digi.ninja zonetransfer.me

; <<>> DiG 9.16.3-Debian <<>> axfr @nsztm1.digi.ninja zonetransfer.me
; (1 server found)
;; global options: +cmd
zonetransfer.me.	7200	IN	SOA	nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600
zonetransfer.me.	300	IN	HINFO	"Casio fx-700G" "Windows XP"
zonetransfer.me.	301	IN	TXT	"google-site-verification=tyP28J7JAUHA9fw2sHXMgcCC0I6XBmmoVi04VlMewxA"
zonetransfer.me.	7200	IN	MX	0 ASPMX.L.GOOGLE.COM.
zonetransfer.me.	7200	IN	MX	10 ALT1.ASPMX.L.GOOGLE.COM.
zonetransfer.me.	7200	IN	MX	10 ALT2.ASPMX.L.GOOGLE.COM.
zonetransfer.me.	7200	IN	MX	20 ASPMX2.GOOGLEMAIL.COM.
zonetransfer.me.	7200	IN	MX	20 ASPMX3.GOOGLEMAIL.COM.
zonetransfer.me.	7200	IN	MX	20 ASPMX4.GOOGLEMAIL.COM.
zonetransfer.me.	7200	IN	MX	20 ASPMX5.GOOGLEMAIL.COM.
zonetransfer.me.	7200	IN	A	5.196.105.14
zonetransfer.me.	7200	IN	NS	nsztm1.digi.ninja.
zonetransfer.me.	7200	IN	NS	nsztm2.digi.ninja.
_acme-challenge.zonetransfer.me. 301 IN	TXT	"6Oa05hbUJ9xSsvYy7pApQvwCUSSGgxvrbdizjePEsZI"
_sip._tcp.zonetransfer.me. 14000 IN	SRV	0 0 5060 www.zonetransfer.me.
14.105.196.5.IN-ADDR.ARPA.zonetransfer.me. 7200	IN PTR www.zonetransfer.me.
asfdbauthdns.zonetransfer.me. 7900 IN	AFSDB	1 asfdbbox.zonetransfer.me.
asfdbbox.zonetransfer.me. 7200	IN	A	127.0.0.1
asfdbvolume.zonetransfer.me. 7800 IN	AFSDB	1 asfdbbox.zonetransfer.me.
canberra-office.zonetransfer.me. 7200 IN A	202.14.81.230
cmdexec.zonetransfer.me. 300	IN	TXT	"; ls"
contact.zonetransfer.me. 2592000 IN	TXT	"Remember to call or email Pippa on +44 123 4567890 or pippa@zonetransfer.me when making DNS changes"
dc-office.zonetransfer.me. 7200	IN	A	143.228.181.132
deadbeef.zonetransfer.me. 7201	IN	AAAA	dead:beaf::
dr.zonetransfer.me.	300	IN	LOC	53 20 56.558 N 1 38 33.526 W 0.00m 1m 10000m 10m
DZC.zonetransfer.me.	7200	IN	TXT	"AbCdEfG"
email.zonetransfer.me.	2222	IN	NAPTR	1 1 "P" "E2U+email" "" email.zonetransfer.me.zonetransfer.me.
email.zonetransfer.me.	7200	IN	A	74.125.206.26
Hello.zonetransfer.me.	7200	IN	TXT	"Hi to Josh and all his class"
home.zonetransfer.me.	7200	IN	A	127.0.0.1
Info.zonetransfer.me.	7200	IN	TXT	"ZoneTransfer.me service provided by Robin Wood - robin@digi.ninja. See http://digi.ninja/projects/zonetransferme.php for more information."
internal.zonetransfer.me. 300	IN	NS	intns1.zonetransfer.me.
internal.zonetransfer.me. 300	IN	NS	intns2.zonetransfer.me.
intns1.zonetransfer.me.	300	IN	A	81.4.108.41
intns2.zonetransfer.me.	300	IN	A	167.88.42.94
office.zonetransfer.me.	7200	IN	A	4.23.39.254
ipv6actnow.org.zonetransfer.me.	7200 IN	AAAA	2001:67c:2e8:11::c100:1332
owa.zonetransfer.me.	7200	IN	A	207.46.197.32
robinwood.zonetransfer.me. 302	IN	TXT	"Robin Wood"
rp.zonetransfer.me.	321	IN	RP	robin.zonetransfer.me. robinwood.zonetransfer.me.
sip.zonetransfer.me.	3333	IN	NAPTR	2 3 "P" "E2U+sip" "!^.*$!sip:customer-service@zonetransfer.me!" .
sqli.zonetransfer.me.	300	IN	TXT	"' or 1=1 --"
sshock.zonetransfer.me.	7200	IN	TXT	"() { :]}; echo ShellShocked"
staging.zonetransfer.me. 7200	IN	CNAME	www.sydneyoperahouse.com.
alltcpportsopen.firewall.test.zonetransfer.me. 301 IN A	127.0.0.1
testing.zonetransfer.me. 301	IN	CNAME	www.zonetransfer.me.
vpn.zonetransfer.me.	4000	IN	A	174.36.59.154
www.zonetransfer.me.	7200	IN	A	5.196.105.14
xss.zonetransfer.me.	300	IN	TXT	"'><script>alert('Boo')</script>"
zonetransfer.me.	7200	IN	SOA	nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600
;; Query time: 312 msec
;; SERVER: 81.4.108.41#53(81.4.108.41)
;; WHEN: Sat Nov 07 10:36:17 EST 2020
;; XFR size: 50 records (messages 1, bytes 1994)

```

```
nsztm1.digi.ninja.
首要的域名服务器

robin.digi.ninja.
管理员邮箱（可作为下一轮攻击储备）
robin@digi.ninja

2019100801
ID号/时间点

172800秒（次要域名服务器会等待时长） 
900秒（如果主要域名服务器获取更新失败后再次尝试中间的等待时间）
1209600秒（等待时长，次要域名服务器获取权威的信息）
3600（TTL Time to Live）

如果摸清routine之后，routine突然更改，证明——系统升级/维护/更新

```