import requests, re

links = [
    "https://www.tiktokv.com/share/video/7396733314398244138/",
    "https://www.tiktokv.com/share/video/7430461089151798571/"
]

def resolve_tiktok(share_link):
    headers = {'User-Agent': 'Mozilla/5.0'}
    resp = requests.get(share_link, headers=headers, allow_redirects=True, timeout=10)
    final = resp.url
    m = re.search(r'(https?://www\.tiktok\.com/(@[\w\.-]+)/video/(\d+))', final)
    if m:
        return {'full_url': m.group(1), 'username': m.group(2), 'video_id': m.group(3)}
    return {'full_url': final, 'username': None, 'video_id': None}

for url in links:
    result = resolve_tiktok(url)
    print(f"{url} → {result['username']}, {result['full_url']}")

<!--
**x0-akm7/X0-akm7** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on learning coding
- 🌱 I’m currently learning more about coding for fun
- 👯 I’m looking to collaborate on new to this wouldn't be much help at the moment 
- 🤔 I’m looking for help with coding in general
- 💬 Ask me about anything
- 📫 How to reach me:here in GitHub sent me a message 
- 😄 Pronouns:She/her
- ⚡ Fun fact: I have 3 cats and a bearded dragon
-->
