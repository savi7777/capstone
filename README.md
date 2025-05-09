services:
  openWebUI:
    image: ghcr.io/open-webui/open-webui:main
    restart: unless-stopped
    ports:
      - "3080:8080"
    extra_hosts:
      - "host.docker.internal:host-gateway"
    volumes:
      - ./open-webui-local:/app/backend/data
    container_name: openwebui
    network_mode: bridge
  ollama:
    image: ollama/ollama
    restart: unless-stopped
    ports:
      - "11434:11434"
    volumes:
      - ./ollama-local:/root/.ollama
    container_name: ollama
    network_mode: bridge
