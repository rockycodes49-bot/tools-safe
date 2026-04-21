#!/usr/bin/python
# << CODE BY ROCKY CODES >>

import json
import requests
import time
import os
import phonenumbers
from phonenumbers import carrier, geocoder, timezone
from sys import stderr

Bl = '\033[30m'
Re = '\033[1;31m'
Gr = '\033[1;32m'
Ye = '\033[1;33m'
Blu = '\033[1;34m'
Mage = '\033[1;35m'
Cy = '\033[1;36m'
Wh = '\033[1;37m'


def is_option(func):
    def wrapper(*args, **kwargs):
        run_banner()
        func(*args, **kwargs)
    return wrapper


@is_option 
def IP_Track():
    ip = input(f"{Wh}\n Enter IP target : {Re}")
    print()
    print(f' {Wh}========== {Gr}IP TRACK DETAILS {Wh}==========')
    req_api = requests.get(f"http://ipwho.is/{ip}")
    ip_data = json.loads(req_api.text)
    time.sleep(2)

    print(f"{Wh}\n IP target       :{Re}", ip)
    print(f"{Wh} Type IP         :{Re}", ip_data["type"])
    print(f"{Wh} Country         :{Re}", ip_data["country"])
    print(f"{Wh} Country Code    :{Re}", ip_data["country_code"])
    print(f"{Wh} City            :{Re}", ip_data["city"])
    print(f"{Wh} Continent       :{Re}", ip_data["continent"])
    print(f"{Wh} Continent Code  :{Re}", ip_data["continent_code"])
    print(f"{Wh} Region          :{Re}", ip_data["region"])
    print(f"{Wh} Region Code     :{Re}", ip_data["region_code"])
    print(f"{Wh} Latitude        :{Re}", ip_data["latitude"])
    print(f"{Wh} Longitude       :{Re}", ip_data["longitude"])

    lat = int(ip_data['latitude'])
    lon = int(ip_data['longitude'])

    print(f"{Wh} Maps            :{Re}", f"https://www.google.com/maps/@{lat},{lon},8z")
    print(f"{Wh} EU              :{Re}", ip_data["is_eu"])
    print(f"{Wh} Postal          :{Re}", ip_data["postal"])
    print(f"{Wh} Calling Code    :{Re}", ip_data["calling_code"])
    print(f"{Wh} Capital         :{Re}", ip_data["capital"])
    print(f"{Wh} Borders         :{Re}", ip_data["borders"])
    print(f"{Wh} Country Flag    :{Re}", ip_data["flag"]["emoji"])
    print(f"{Wh} ASN             :{Re}", ip_data["connection"]["asn"])
    print(f"{Wh} ORG             :{Re}", ip_data["connection"]["org"])
    print(f"{Wh} ISP             :{Re}", ip_data["connection"]["isp"])
    print(f"{Wh} Domain          :{Re}", ip_data["connection"]["domain"])
    print(f"{Wh} Timezone ID     :{Re}", ip_data["timezone"]["id"])
    print(f"{Wh} Current Time    :{Re}", ip_data["timezone"]["current_time"])


@is_option
def phoneGW():
    User_phone = input(f"\n {Wh}Enter phone number {Re}(+91xxxx) {Wh}: {Re}")
    default_region = "ID"

    parsed_number = phonenumbers.parse(User_phone, default_region)

    region_code = phonenumbers.region_code_for_number(parsed_number)
    provider = carrier.name_for_number(parsed_number, "en")
    location = geocoder.description_for_number(parsed_number, "en")
    timezoneF = ', '.join(timezone.time_zones_for_number(parsed_number))

    print(f"\n {Wh}========== {Gr}PHONE NUMBER DETAILS {Wh}==========")
    print(f"{Wh} Location   :{Re} {location}")
    print(f"{Wh} Region     :{Re} {region_code}")
    print(f"{Wh} Timezone   :{Re} {timezoneF}")
    print(f"{Wh} Operator   :{Re} {provider}")
    print(f"{Wh} Valid      :{Re} {phonenumbers.is_valid_number(parsed_number)}")


@is_option
def TrackLu():
    try:
        username = input(f"\n {Wh}Enter Username : {Re}")
        print(f"\n {Wh}========== {Gr}USERNAME SEARCH RESULT {Wh}==========\n")

        sites = [
            "https://www.instagram.com/{}",
            "https://www.github.com/{}",
            "https://www.twitter.com/{}",
            "https://www.tiktok.com/@{}"
        ]

        for site in sites:
            url = site.format(username)
            r = requests.get(url)
            if r.status_code == 200:
                print(f"{Gr}[FOUND]{Wh} {url}")
            else:
                print(f"{Re}[NOT FOUND]{Wh} {url}")

    except Exception as e:
        print(f"{Re}Error : {e}")


@is_option
def showIP():
    ip = requests.get('https://api.ipify.org/').text
    print(f"\n {Wh}========== {Gr}YOUR IP INFORMATION {Wh}==========")
    print(f"\n {Wh}[ + ] Your IP : {Re}{ip}")


options = [
    {'num': 1, 'text': 'IP Tracker', 'func': IP_Track},
    {'num': 2, 'text': 'Show Your IP', 'func': showIP},
    {'num': 3, 'text': 'Phone Tracker', 'func': phoneGW},
    {'num': 4, 'text': 'Username Tracker', 'func': TrackLu},
    {'num': 0, 'text': 'Exit', 'func': exit}
]


def clear():
    os.system('cls' if os.name == 'nt' else 'clear')


def option():
    clear()
    stderr.writelines(f"""
██████╗  ██████╗  ██████╗██╗  ██╗██╗   ██╗
██╔══██╗██╔═══██╗██╔════╝██║ ██╔╝╚██╗ ██╔╝
██████╔╝██║   ██║██║     █████╔╝  ╚████╔╝ 
██╔══██╗██║   ██║██║     ██╔═██╗   ╚██╔╝  
██║  ██║╚██████╔╝╚██████╗██║  ██╗   ██║   
╚═╝  ╚═╝ ╚═════╝  ╚═════╝╚═╝  ╚═╝   ╚═╝   

   {Gr}[ 🔥 ] ROCKY CODES TOOL [ 🔥 ]
   {Ye}Developer : Rocky Bhai

""")

    for opt in options:
        print(f"{Wh}[ {opt['num']} ] {Gr}{opt['text']}")


def run_banner():
    clear()
    stderr.writelines(f"""{Wh}
----------------------------------------
 {Gr}ROCKY CODES TRACKER
 {Ye}DEV : @ROCKY_CODES
----------------------------------------
""")


def main():
    while True:
        option()
        try:
            opt = int(input(f"\n{Wh}Select Option : {Re}"))

            for o in options:
                if o['num'] == opt:
                    o['func']()
                    break

            input(f"\n{Wh}Press Enter to continue...")

        except:
            print(f"{Re}Invalid input!")
            time.sleep(1)


if __name__ == '__main__':
    main()
