# CVE-2023-43261 - PoC
### Critical Vulnerability Exposes Sensitive Information and Enables Unauthorized Access in Milesight Routers 

- **Date:** 1 October 2023 
- **Vendor of the product:** [Milesight](https://www.milesight.com/) (Formerly Xiamen Ursalink Technology Co., Ltd.)
- **Affected Products:** UR5X, UR32L, UR32, UR35, UR41 and there might be other Industrial Cellular Routers that could also be vulnerable.
- **Affected Firmware:** I've confirmed the patch for firmware v35.3.0.7. Earlier versions may be vulnerable, but vendor confirmation is needed. I have made the request, but I have not received a response yet.
- **Severity:** 7.3/10 - ![Alt text](https://img.shields.io/badge/-High-df3d03) 

A critical security vulnerability has been identified in Milesight Industrial Cellular Routers, compromising the security of sensitive credentials and permitting unauthorized access. This vulnerability stems from a misconfiguration that results in directory listing being enabled on the router systems, rendering log files publicly accessible. These log files, while containing sensitive information such as admin and other user passwords (encrypted as a security measure), can be exploited by attackers via the router's web interface. The presence of a hardcoded AES secret key and initialization vector (IV) in the JavaScript code further exacerbates the situation, facilitating the decryption of these passwords. This chain of vulnerabilities allows malicious actors to gain unauthorized access to the router.

## Usage
Run the script with the following command, replacing `<URL>` with your target URL.

```console
foo@bar:~$ python3 CVE-2023-43261.py <URL>
```

Run the script with the following command to process a list of URLs in the file:

```console
foo@bar:~$ python3 CVE-2023-43261.py -f list_urls.txt
```

![152023-09-16_15-10](https://github.com/win3zz/CVE-2023-43261/assets/12781459/2c824c37-90a9-4ec5-b5fc-3f3a13542d70)


## Google Dorks
- ```"/lang/log/system" ext:log```
- ```"URSALINK" "English" "Login"```

## Shodan Search Query

- ```http.html:rt_title```

## References 
1. Security Advisory: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-43261
2. Writeup: https://medium.com/@win3zz/inside-the-router-how-i-accessed-industrial-routers-and-reported-the-flaws-29c34213dfdf

**Script Author:** Bipin Jitiya ([@win3zz](https://twitter.com/win3zz))

---

![DISCLAIMER](https://readme-typing-svg.demolab.com/?font=Roboto&weight=900&size=24&pause=1000&color=FF0000&width=435&lines=DISCLAIMER)

The PoC script provided in this repository is intended for educational and research purposes only. It is designed to demonstrate the existence of a vulnerability and assist in understanding potential security risks.

**Usage of this script for any unauthorized activities, including but not limited to unauthorized access, unauthorized testing, or any other form of misuse, is strictly prohibited.**

The author and contributors of this repository assume no liability and are not responsible for any misuse or damages caused by the utilization of this script. By using this script, you agree to use it responsibly and at your own risk.

Always obtain proper authorization and permissions before conducting any security assessments or penetration testing activities. Ensure that you comply with all applicable laws, regulations, and ethical guidelines.
